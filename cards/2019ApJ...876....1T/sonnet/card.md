# CNO Emission of an Unlensed Submillimeter Galaxy at z = 4.3

`2019ApJ...876....1T` | The Astrophysical Journal 2019 | first author: Tadaki, Ken-ichi | arXiv: 1903.11234 | DOI: 10.3847/1538-4357/ab1415

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: What are the spatial extent, kinematics, PDR/ionized gas conditions and gas-phase metallicity of the unlensed SMG COSMOS-AzTEC-1 from CNO fine-structure lines?  
  > "to study the spatial extent of the FIR fine structure lines and the physical conditions of gas in the PDRs and the ionized regions." (Introduction)
- Target **COSMOS-AzTEC-1**: coordinates _not stated_; z/distance z=4.342  
  > "an extreme starburst galaxy at $z=4.342$, COSMOS-AZTEC-1 hereafter" (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2017.1.00300.S, 2018.1.00081.S, 2017.1.00127.S
- bands: Band 3 (CO 4-3), Band 6 ([N II]), Band 7 ([C II]), Band 9 ([O III])  
  > "we have made new observations of the [N ii] 205 $\mu$m, [C ii] 158 $\mu$m, and [O iii] 88 $\mu$m lines with Band-6, 7, 9, respectively." (Observations and results)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 12–4664, 14–1277, 18–2967, 32–2017 kλ (Bands 3,6,7,9)  
  > "| baseline length | (k$\lambda$) | 12–4664 | 14–1277 | 18–2967 | 32–2017 |" (Table 1)
- angular resolution: 0.3'' and 0.9'' cubes  
  > "We create two cubes with different resolutions (0.3$''$ and 0.9$''$), corresponding to 1 kpc and 3 kpc in radius" (Observations and results)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 420, 300, 32, 100 min for Bands 3, 6, 7, 9  
  > "| on-source time | (min) | 420 | 300 | 32 | 100 |" (Table 1)
- observing dates: 2017/10,11 (B3); 2018/11 (B6); 2017/12 (B7); 2018/11,12 (B9)  
  > "| observation date | | 2017/10,11 | 2018/11 | 2017/12 | 2018/11,12 |" (Table 1)
- pi or archival as stated: _not stated_
- Line: CO 4-3 (not stated)
- Line: [N II] 205 μm (not stated)
- Line: [C II] 158 μm (not stated)
- Line: [O III] 88 μm (not stated)
- External data: Band-3 CO(4-3) data and Band-4 (2 mm) continuum  
  > "Following our previous observations of the CO(4-3) emission line with ALMA Band-3 receivers" (Observations and results) [from (cite: 2018Natur.560..613T)]
- External data: PDR model grid predictions  
  > "By comparing our measurements with values predicted by theoretical models of (cite: 1999ApJ...527..795K)" (3.3 Gas properties in PDR) [from (cite: 1999ApJ...527..795K)]
- External data: Stellar mass M*~1e11 Msun  
  > "Given the stellar mass of $M_\star\sim10^{11}~M_\odot$ in COSMOS-AzTEC-1 (cite: 2018Natur.560..613T)" (3.4 Gas-phase metallicity) [from (cite: 2018Natur.560..613T)]

## Processing

### Calibration

- pipeline or manual: standard manner using CASA  
  > "The data were calibrated in the standard manner using `CASA` (cite: 2007ASPC..376..127M)." (Observations and results)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 5% Band 3,4; 10% Band 6,7; 20% Band 9  
  > "flux calibration errors (5% at Band-3,4, 10% at Band-6,7, 20% at Band-9; ALMA Technical Handbook)" (3.2 Far-infrared luminosities)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: 0.3'': 0.2'' (B3), n/a (B6), 0.2'' (B7), 0.1'' (B9); 0.9'': 0.6, 0.4, 0.5, 0.5''  
  > "| *uv* tapering for $0.3^{\prime\prime}$-resolution maps | 0.2$^{\prime\prime}$ | n/a | 0.2$^{\prime\prime}$ | 0.1$^{\prime\prime}$ |" (Table 1)
- cell size: _not stated_
- image size: _not stated_
- masking: circular mask 1.5'' diameter, cleaned to 1σ, 50 km/s channels  
  > "We cleaned the cubes with a channel width of 50 km s$^{-1}$ down to the 1$\sigma$ level in a circular mask with a diameter of 1.5$''$." (Observations and results)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: uv tapering and Gaussian smoothing  
  > "by applying a *uv* tapering and Gaussian smoothing" (Observations and results)
- final beam: _not stated_
- final rms: 0.3'': 0.10, 0.09, 0.41, 1.5 mJy/beam per 50 km/s; 89 μm continuum 0.43 mJy/beam  
  > "The noise level is 0.43 mJy beam$^{-1}$." (Observations and results)

### Inherited from earlier work

- Band-3 CO(4-3) and Band-4 observations  
  > "Following our previous observations of the CO(4-3) emission line with ALMA Band-3 receivers" (Observations and results) [from (cite: 2018Natur.560..613T)]
- Cloudy abundance patterns and parameters  
  > "Gas element abundance patterns and other parameters in the Cloudy run are the same as the previous calculations by (cite: 2011A&A...526A.149N)." (3.4 Gas-phase metallicity) [from (cite: 2011A&A...526A.149N)]
- 10% systematic errors on kinematic fits  
  > "shows systematic errors of $\sim$10% in all parameters (Tadaki et al. in prep)" (3.1 Gas kinematics) [from Tadaki et al. in prep]

### Not stated but needed to reproduce (our reading)

- CASA version and tclean parameters (weighting, robust, deconvolver)
- Continuum subtraction and line-free channels
- Gaussian smoothing kernel and exact beams
- Flux calibrators and self-calibration
- GalPaK3D priors/setup and UVMULTIFIT model details
- CIGALE parameter grids and priors
- Cloudy grid ranges and the exact procedure converting n_H^PDR,G0 to ion parameters
- Aperture definitions for 1 kpc and 3 kpc luminosities
- Cosmology adopted

## Analysis recipe

1. **Make cubes and moment maps**: Taper and smooth to 0.3'' and 0.9'' cubes, clean at 50 km/s; immoments for -250 to +250 km/s  
  > "in the same velocity range between –250 km s$^{-1}$ and +250 km s$^{-1}$ using the `CASA/immoments` task" (Observations and results)
   - software: CASA
   - parameter: 2σ mask for velocity field and dispersion maps  
  > "A 2$\sigma$ masking threshold was adopted for the velocity field and velocity dispersion maps." (Observations and results)
   - fitting: _not stated_
   - validation: [O III] detection checked via max S/N pixel in primary beam and negative peak -2.8σ  
  > "the maximum negative peak is identified at the level of -2.8$\sigma$, the [O iii] detection should be real." (Observations and results)
2. **Fit disk kinematics and sizes**: 3D thick exponential disk with arctan rotation curve, constant σ0; inclination/PA fixed to [CII] values for CO and [NII]  
  > "We assume an arctan rotation curve and a constant $\sigma_0$ within a galaxy in the models." (3.1 Gas kinematics)
   - software: GalPaK3D, UVMULTIFIT
   - parameter: MCMC 20,000 iterations  
  > "based on the 95th percentile of the last 60% of the Markov chain Monte Carlo (MCMC) chain for 20,000 iterations" (3.1 Gas kinematics)
   - fitting: MCMC in GalPaK3D; visibility fits of exponential disks with UVMULTIFIT  
  > "we fit the visibility data to exponential disk models using `UVMULTIFIT` code" (3.1 Gas kinematics)
   - validation: Compared image-plane and visibility half-light radii  
  > "The half-light radii are similar between the two methods" (3.1 Gas kinematics)
3. **Derive FIR luminosity and dust temperature**: SED fit of 10 (1 kpc) or 12 (3 kpc) bands with single modified blackbody plus power law  
  > "We adopt a simple analytic model with a single modified black body radiation, characterized by dust temperature $T_\mathrm{dust}$ and an emissivity index $\beta$, and a power-low emission" (3.2 Far-infrared luminosities)
   - software: CIGALE
   - parameter: L_FIR over rest 42.5–122.5 μm  
  > "rest-frame wavelength range of 42.5 $\mu$m–122.5 $\mu$m" (3.2 Far-infrared luminosities)
   - fitting: _not stated_
   - validation: _not stated_
4. **Constrain PDR density and G0**: Chi-square of [CII]PDR/FIR and [CII]PDR/CO against Kaufman et al. models over n_H=10^3-7, G0=10^1-6  
  > "we compute chi-square values for two luminosity ratios of [C ii]$^\mathrm{PDR}$/FIR and [C ii]$^\mathrm{PDR}$/CO" (3.3 Gas properties in PDR)
   - parameter: CO luminosity multiplied by 2; [CII]ion/[NII]=2  
  > "we increase the observed CO luminosities by a factor of two to count the emission from the far side." (3.3 Gas properties in PDR)
   - assumption: Plane-parallel slab PDRs; [CII] and dust optically thin, CO thick  
  > "[C ii] line and dust continuum emission are generally optically thin while CO emission is optically thick." (3.3 Gas properties in PDR)
   - fitting: _not stated_
   - validation: _not stated_
5. **Infer gas metallicity from [OIII]/[NII]**: Cloudy photoionization grid in n_H^ion, U, Z with BPASS 1 Myr constant SF input; stellar Z = gas Z/5  
  > "We generate the input spectra of a constant star formation model with an age of 1 Myr by using Binary Population and Spectral Synthesis (`BPASS v2.0`) code" (3.4 Gas-phase metallicity)
   - software: Cloudy, BPASS
   - assumption: Stellar metallicity lower than gas-phase by factor 5  
  > "We also assume that the stellar metallicity is lower than gas-phase metallicity by a factor of 5" (3.4 Gas-phase metallicity)
   - fitting: _not stated_
   - validation: Compared with z=3-4 mass–metallicity relation extrapolation  
  > "gives $Z_\mathrm{gas}\sim1.0~Z_\odot$ for massive galaxies with $M_\star=10^{11}~M_\odot$, which is consistent with our measurement." (3.4 Gas-phase metallicity)

## Software

- **CASA** : calibration, imaging, immoments  
  > "The data were calibrated in the standard manner using `CASA`" (Observations and results)
- **GalPaK3D** v1.9.1: 3D disk kinematic modeling  
  > "using the `GalPaK3D v1.9.1` code" (3.1 Gas kinematics)
- **UVMULTIFIT** : visibility-plane size fits  
  > "using `UVMULTIFIT` code" (3.1 Gas kinematics)
- **CIGALE** : SED fitting for L_FIR  
  > "using the `CIGALE` code" (3.2 Far-infrared luminosities)
- **Cloudy** v17.01: photoionization modeling  
  > "We use the spectral synthesis code `Cloudy v17.01`" (3.4 Gas-phase metallicity)
- **BPASS** v2.0: input stellar spectra  
  > "Binary Population and Spectral Synthesis (`BPASS v2.0`) code" (3.4 Gas-phase metallicity)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Inclination (from [CII]) | 41.8 | ±0.2 | degree | 2 | the inclination is 41.8$\pm0.2$ degree |
| L_FIR (1 kpc) | 5.3e12 | ±1.1e12 | Lsun | 3 | $L_\mathrm{FIR}=5.3\pm1.1\times10^{12}~L_\odot$ |
| T_dust (1 kpc) | 59 | +5/-7 | K | 3 | $T_\mathrm{dust}=59^{+5}_{-7}$ K |
| 89 μm continuum half-light radius | 0.81 | ±0.04 | kpc | 2 | $R_\mathrm{1/2,visibility}=$0.81$\pm$0.04 kpc |
| L[OIII]/L[NII] (3 kpc) | 6.4 | ±2.2 | dimensionless | 5 | $L_\mathrm{[OIII]}/L_\mathrm{[NII]}=6.4\pm2.2$ |
| Gas metallicity | 0.7-1.0 | not stated | Zsun | 5 | $Z_\mathrm{gas}=0.7-1.0~Z_\odot$ |
| Vmax/σ0 | 2.5–2.8 | not stated | dimensionless | 2 | $V_\mathrm{max}/\sigma_0$=2.5–2.8 |

## Qualitative findings

- [CII] is most extended and dust most compact; kinematics of CO, [NII], [CII] agree  
  > "the [C ii] emitting gas is the most extended and the dust is the most compact" (abstract)

## Claim tuples

- H: Do ionized, PDR and molecular gas share the same gravitational potential? | E: GalPaK3D fits to CO, [NII], [CII] cubes | R: Similar Vmax (~217-234 km/s) and σ0 | F: Same potential; rotation-dominated | **supported**
- H: What are PDR conditions? | E: Chi-square PDR model comparison after removing ionized [CII] | R: n_H=10^5.5-5.75, G0=10^3.5-3.75 (1 kpc); 10^5.0-5.25, 10^3.25-3.5 (3 kpc) | F: Dense PDRs with higher density in center | **supported**
- H: What is the gas metallicity? | E: [OIII]/[NII] with Cloudy models | R: ratio 6.4±2.2 | F: Near-solar Z=0.7-1.0 Zsun, chemically evolved | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Metallicity assumes OB stars associated with dense PDRs; ionized gas density not directly measured  
  > "our metallicity measurements are based on the assumption that ionizing sources (OB stars) are all associated with dense PDRs" (Discussion)
- Caveat (inferred, ours): [OIII] detection is only ~4σ and tentative
- Caveat (inferred, ours): Metallicity depends on model assumptions (stellar Z offset, ionized gas density tied to PDR)
- Caveat (inferred, ours): Fixed [CII]ion/[NII]=2 affects PDR fraction

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Imaging and calibration parameters
- Missing: SED and Cloudy grid details
- Missing: Systematics paper in prep
- Data volume (inferred): ~hundreds of GB across four bands
- Score (inferred): 3/5, Codes named, but many imaging and modeling parameters are missing and the systematics paper is in prep.
- Rediscovery candidate: no, Recipe is incomplete for the modeling steps and public data status is not stated.

## Links

- Method: (cite: 2015AJ....150...92B) (GalPaK3D)
- Method: (cite: 1999ApJ...527..795K) (PDR models)
- Companion: (cite: 2018Natur.560..613T) (previous CO(4-3) and Band-4 observations of AzTEC-1)

## Checks

```json
{
 "quotes": 60,
 "quotes_ok": 60,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 78,
  "stated": 42,
  "rate": 0.538
 },
 "evidence_ok": true
}
```
