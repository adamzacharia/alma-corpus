# Morphology and Kinematics of Warm Molecular Gas in the Nuclear Region of Arp 220 as Revealed by ALMA

`2015ApJ...806...17R` | The Astrophysical Journal 2015 | first author: Rangwala, Naseem | arXiv: 1504.01773 | DOI: 10.1088/0004-637X/806/1/17

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, milky_way_ism
- Question: What are the morphology and kinematics of the warm (CO J=6-5) molecular gas in the two nuclei of Arp 220, and what energy source heats it?  
  > "In this paper, we present the first high-resolution and high-S/N maps of the warm molecular gas in Arp 220 using the CO $J=6-5$ line." (1 Introduction)
- Target **Arp 220 (eastern and western nuclei)**: coordinates East (CO peak): 15:34:57.30 +23:30:11.53; West: 15:34:57.22 +23:30:11.68 (J2000)  
  > "As the closest example ($D = 77$ Mpc, 1$''$ = 373 pc) of an ultra-luminous infrared galaxy (ULIRG), Arp 220 has been studied intensively" (1 Introduction); "| Peak flux location | (15:34:57.30, +23:30:11.53) | (15:34:57.22, +23:30:11.68) | J2000 |" (Table 1); z/distance z = 0.01813; D = 77 Mpc (1" = 373 pc)  
  > "As the closest example ($D = 77$ Mpc, 1$''$ = 373 pc) of an ultra-luminous infrared galaxy (ULIRG), Arp 220 has been studied intensively" (1 Introduction); "| Peak flux location | (15:34:57.30, +23:30:11.53) | (15:34:57.22, +23:30:11.68) | J2000 |" (Table 1); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00403.S
- bands: Band 9  
  > "The Band 9 receivers were tuned to cover the CO J=6-5 transition (rest frequency 691.473 GHz" (2 Observations and Data Reduction)
- frequencies and spectral setup: TDM mode, 15.625 MHz spectral resolution; cube at 10 km/s  
  > "The correlator was configured in low-resolution wide-bandwidth TDM mode to give a spectral resolution of 15.625 MHz." (2 Observations and Data Reduction)
- continuum bandwidth: total bandwidth 8 GHz, four spectral windows (usable bandwidth reduced)  
  > "with a total bandwidth of 8 GHz; however, the usable bandwidth was somewhat reduced" (2 Observations and Data Reduction)
- arrays: _not stated_
- configurations: extended/hybrid configuration, Cycle 0  
  > "at the end of cycle-0 in an extended/hybrid configuration" (2 Observations and Data Reduction)
- baselines: 13 to 374 m  
  > "The observations covered projected baselines from 13 to 374 m." (2 Observations and Data Reduction)
- angular resolution: 0.39" x 0.22" (PA 28 deg), uniform weighting  
  > "all channels would have the same beam ($0.39\ensuremath{'' } \times 0.22\ensuremath{''}$) at position angle 28$^{\circ}$" (2 Observations and Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: 1 sigma 30 mJy/beam (0.9 K) per channel in uniform cube  
  > "The typical 1$\sigma$ noise in the cleaned uniform cube is 30 mJy beam$^{-1}$ or 0.9 K per channel." (2 Observations and Data Reduction)
- time on source: 44.4 minutes, 23 antennas  
  > "The total on-source integration time was 44.4 minutes using 23 antennas." (2 Observations and Data Reduction)
- observing dates: 2012 December 31  
  > "Arp 220 was observed with ALMA on 2012 December 31" (2 Observations and Data Reduction)
- pi or archival as stated: _not stated_
- Line: CO J=6-5 (691.473 GHz)
- Line: SiO J=16-15 (694.293 GHz)
- Other facility **Herschel SPIRE-FTS**: Total CO 6-5 flux and warm-gas M/L ratio from CO SLED modeling  
  > "We determined the mass of the warm molecular gas (listed in Table 1) in the individual nuclei using the information from our *Herschel* SPIRE-FTS observations" (6 Warm Molecular Gas Mass and Luminosity)
- Other facility **SMA (Sakamoto CO 3-2 cube)**: CO J=3-2 profile at 0.3" for comparison  
  > "We thank Kazushi Sakamoto for sharing his CO $J=3-2$ data cube observed by the Submillimeter Array." (Acknowledgments)
- External data: Warm-gas mass to CO 6-5 luminosity ratio of 21 Msun/Lsun  
  > "$M(H_2)_\mathrm{warm}/L_{CO6-5} = 21$ M$_{\odot}$/L$_{\odot}$ derived from Herschel FTS CO SLED" (Table 1) [from Rangwala et al. 2011 (cite: rangwala2011)]
- External data: L_FIR and continuum sizes, dust masses, temperatures, inclination 50 deg for nuclei  
  > "Using the $L_{\mathrm{FIR}}$ measured from the ALMA 691 GHz continuum emission in Paper I." (Table 1) [from Wilson et al. 2014 (cite: wilson14)]
- External data: Inclination 50 deg from 33 GHz continuum disk fit  
  > "for an inclination of $50^\circ$, obtained by (cite: barcosmunoz14)" (5 Dynamical Mass and Disk Stability) [from (cite: barcosmunoz14)]
- External data: Supernova rate 4 +/- 2 per year  
  > "Using the observed supernovae rate of $\nu_{\rm SN} = 4 \pm 2$ per year (cite: lonsdale06)" (6 Warm Molecular Gas Mass and Luminosity) [from (cite: lonsdale06)]

## Processing

### Calibration

- pipeline or manual: Flagged, calibrated and imaged by ALMA staff; custom procedure for low-S/N phase calibrators  
  > "The data were flagged, calibrated, and imaged by ALMA staff prior to delivery." (2 Observations and Data Reduction)
- casa version: CASA 4.1.0  
  > "made new, cleaned data cubes following the same steps carried out by ALMA staff using CASA version 4.1.0" (2 Observations and Data Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: No absolute flux calibrator; 3C279 bandpass calibrator set to 6.0 Jy from Band 9 observation within one day  
  > "The absolute flux scale was set using a flux of 6.0 Jy for the bandpass calibrator, 3C279, determined by a Band 9 observation taken within one day of these observations." (2 Observations and Data Reduction)
- flux scale uncertainty: about 15% for ALMA  
  > "(about 10% for Herschel-SPIRE and 15% for ALMA)" (2 Observations and Data Reduction)
- self calibration: Two rounds of phase-only (natural weighting), then one amplitude+phase round; noise 36->16 mJy/beam (line-free), 100->18 mJy/beam (line channels)  
  > "we carried out two rounds of phase-only self-calibration using natural weighting and a relatively small clean box to include emission from the bright central region." (2 Observations and Data Reduction)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: uniform and natural weighting cubes  
  > "We made image cubes with both natural and uniform weighting to maximize sensitivity and angular resolution, respectively." (2 Observations and Data Reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Clean boxes adjusted with frequency to include all significant emission  
  > "the clean box was adjusted with frequency to include all regions with significant emission" (2 Observations and Data Reduction)
- multiscale scales: _not stated_
- continuum subtraction: Zeroth-order fit to most channels in the two spectral windows away from bright CO  
  > "we carried out continuum subtraction using a zeroth order fit to most of the channels in the two spectral windows located away from the bright CO emission" (2 Observations and Data Reduction)
- line free channels: _not stated_
- primary beam correction: Small correction applied to fluxes  
  > "After a small correction for primary beam attenuation, the total integrated CO $J=6-5$ flux is 3670 Jy km s$^{-1}$." (2 Observations and Data Reduction)
- array combination: _not stated_
- smoothing: Uniform cube smoothed to a common beam  
  > "As a final step, the uniform cube was smoothed slightly so that all channels would have the same beam" (2 Observations and Data Reduction)
- final beam: 0.39" x 0.22", PA 28 deg (uniform); 0.447" x 0.273" natural  
  > "with a beam size of $0.447\ensuremath{''} \times 0.273\ensuremath{''}$ ($\mathrm{PA} = 28^{\circ}$)" (Table 1)
- final rms: 30 mJy/beam per 10 km/s channel (uniform)  
  > "The typical 1$\sigma$ noise in the cleaned uniform cube is 30 mJy beam$^{-1}$ or 0.9 K per channel." (2 Observations and Data Reduction)

### Inherited from earlier work

- Continuum velocity ranges/images and dust properties (L_FIR, sizes, gas mass, surface density, PA 28-36 deg)  
  > "adjusted the velocity ranges used to make the continuum images (cite: wilson14) to avoid all emission and absorption features." (2 Observations and Data Reduction) [from Paper I (cite: wilson14)]
- Calibration steps followed ALMA staff reduction, including self-calibration method  
  > "Following their method, we carried out two rounds of phase-only self-calibration" (2 Observations and Data Reduction) [from ALMA staff reduction notes]
- Warm gas M/L ratio  
  > "This ratio $M$(H$_{2}$)/$L_{\mathrm{CO}}$(6-5) is about 21 M$_{\odot}$/L$_{\odot}$." (6 Warm Molecular Gas Mass and Luminosity) [from (cite: rangwala2011)]

### Not stated but needed to reproduce (our reading)

- Clean thresholds, iteration counts and clean box definitions
- Cell size and image size
- Line-free channels used for continuum subtraction
- Self-calibration solution intervals
- Robust/weighting details beyond natural vs uniform
- Optimization method for choosing kinematic model parameters (apparently by eye)
- Rotation curve tabulation for model
- Moment-map clipping thresholds
- Data cube product not released

## Analysis recipe

1. **Re-image calibrated data and self-calibrate**: Re-clean delivered calibrated uv data with adjusted clean boxes, self-calibration, continuum subtraction, uniform and natural cubes at 10 km/s  
  > "we began with the delivered calibrated $uv$ data and made new, cleaned data cubes following the same steps carried out by ALMA staff using CASA version 4.1.0." (2 Observations and Data Reduction)
   - software: CASA
   - parameter: 10 km/s channels; beam 0.39"x0.22"  
  > "We used a velocity resolution of 10 km s$^{-1}$ for the CO data cube." (2 Observations and Data Reduction)
   - fitting: _not stated_
   - validation: Total CO 6-5 flux 3670 Jy km/s compared with Herschel 4070 +/- 80  
  > "This value is in agreement with the total flux obtained from *Herschel*-SPIRE of $4070 \pm 80$ Jy km s$^{-1}$" (2 Observations and Data Reduction)
2. **Measure nuclear morphology and line properties**: Moment maps (integrated, velocity, dispersion, peak) and Gaussian fits to the nuclei  
  > "A simple Gaussian fitting to the two nuclei shows that the western nucleus is almost circular" (3 Observed Morphology and Kinematics)
   - assumption: 1" = 373 pc  
  > "(205 pc using 1$''$ = 373 pc)" (3 Observed Morphology and Kinematics)
   - fitting: Gaussian fits  
  > "A simple Gaussian fitting to the two nuclei shows that the western nucleus is almost circular with a deconvolved size (FWHM)" (Observed Morphology and Kinematics of the Warm Molecular Gas)
   - validation: _not stated_
3. **Model eastern nuclear disk line profiles**: 2D edge-on axisymmetric rotating disk radiative transfer with Gaussian line/dust source functions and optical depths, beam-convolved; variants with foreground absorber or outflow  
  > "For simplicity, we assume that the disk is perfectly edge-on." (4 Modeling)
   - software: RADEX
   - parameter: tau_0,l=4, tau_0,d=1, sigma=85 km/s, V_c=135 km/s with inner bump peaking ~240 km/s  
  > "center-to-edge line center optical depth $\tau_{0,l}=4$, dust optical depth $\tau_{0,d}=1$, velocity dispersion $\sigma = 85$ km s$^{-1}$" (4.1 Model Results)
   - assumption: Disk uniform vertically; inclination ~50 deg ignored  
  > "We also assume that the disk is uniform in the vertical direction" (4 Modeling)
   - fitting: Manual comparison of model and observed profiles; no formal fit  
  > "A reasonable match to the observed profiles for the eastern nucleus is provided by a model" (4.1 Model Results)
   - validation: Compared with IWMV curve from moment-1; absorption model preferred over outflow  
  > "Hence the observed IWMV curve is completely consistent with an underlying axisymmetric disk model" (4.4)
4. **Dynamical mass and Toomre Q**: Rotation and dispersion in quadrature for M_dyn within 220 pc; Toomre Q with sigma as sound speed  
  > "Adding the asymptotic rotation velocity (135 km s$^{-1}$) and velocity dispersion (85 km s$^{-1}$) in quadrature" (5 Dynamical Mass and Disk Stability)
   - assumption: Inclination 50 deg for upper mass  
  > "where the larger number is obtained by correcting the rotation velocity (but not the velocity dispersion) for an inclination of $50^\circ$" (Dynamical Mass and Disk Stability)
   - fitting: _not stated_
   - validation: Compared with gas mass 1.1e9 Msun from Paper I  
  > "this enclosed mass is in agreement with the total molecular gas mass of $1.1 \times 10^{9}$ derived in Paper I from the continuum emission" (Dynamical Mass and Disk Stability)
5. **Warm gas mass and L_CO/L_FIR**: Multiply CO 6-5 luminosity by M/L=21 Msun/Lsun; ratio to L_FIR from Paper I  
  > "Using this ratio and the individual integrated CO $J=6-5$ ALMA fluxes for the two nuclei we estimate the warm molecular gas mass" (6)
   - assumption: Herschel global ratio applies to each nucleus  
  > "this ratio is an average quantity over the whole system and is likely to vary spatially" (footnote 5)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.1.0: Imaging, self-calibration, continuum subtraction  
  > "following the same steps carried out by ALMA staff using CASA version 4.1.0" (2 Observations and Data Reduction)
- **RADEX** : Exploratory non-LTE modeling of absorber parameters  
  > "Exploratory non-LTE modeling using RADEX (cite: tak07) of plausible absorber parameters" (4.4)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total integrated CO 6-5 flux | 3670 | ~15% systematic | Jy km/s | 1 | the total integrated CO $J=6-5$ flux is 3670 Jy km s$^{-1}$ |
| Warm gas mass east / west | 1.4e8 / 1.6e8 | not stated | Msun | 5 | / Warm Gas Mass$^{b}$ / $1.4 \times 10^{8}$ / $1.6 \times 10^{8}$ / $M_{\odot}$ / |
| L_CO/L_FIR east / west | 6.7e-5 / 6.0e-6 | +16/-4.4e-5 ; +29/-3.6e-6 | dimensionless | 5 | $6.7^{+16}_{-4.4} \times 10^{-5}$ / $6.0^{+29}_{-3.6} \times 10^{-6}$ |
| Peak velocity dispersion east / west | 175 / 160 | not stated | km/s | 2 | with values as large as 175 km s$^{-1}$ and 160 km s$^{-1}$ for the eastern and western nucleus |
| Eastern nucleus dynamical mass within 220 pc | 1.6-2.9e9 | not stated | Msun | 4 | we derive a dynamical mass within $r = 220$ pc of $M_\mathrm{tot}\sim 1.6 - 2.9
\times 10^9 M_\odot$ |
| Toomre Q eastern nucleus | ~1.5 | factor of two | dimensionless | 4 | we find $Q\sim 1.5$; this number should be regarded as uncertain by at least a factor of two |
| Absorber mass | few x (1e7-1e8) | not stated | Msun | 3 | M_{abs}\sim {\rm \ few}\times \left(10^7 - 10^8\right) M_\odot. |
| SiO 16-15 mean absorption depth, west | -0.23 | not stated | Jy/beam | 2 | The mean depth of the absorption in the central 200 km s$^{-1}$ of the line is -0.23 Jy beam$^{-1}$ or -6.9 K. |

## Qualitative findings

- CO 6-5 peak is offset ~100 pc from the continuum peak in both nuclei, in the same direction, likely due to foreground absorption of the SW sides  
  > "the peak of the line emission is offset from the peak of the continuum emission in both nuclei by about 100 pc in the same direction" (abstract)
- Strong redshifted CO absorption near the SW of each nucleus; SiO 16-15 absorption only toward the western nucleus  
  > "We also clearly detect strong, highly redshifted CO absorption located near the southwest side of each nucleus." (abstract)

## Claim tuples

- H: Do line asymmetries and line-to-continuum offset arise from foreground absorption rather than outflow? | E: Rotating disk model with foreground absorber vs with outflow compared to profiles and IWMV curve | R: Both fit acceptably; absorption matches IWMV and profiles better | F: Absorption favored, absorber mass comparable to warm gas mass | **partially**
- H: Is the eastern nucleus CO-overluminous relative to FIR, implying extra heating? | E: Compare L_CO6-5/L_FIR between nuclei | R: 6.7e-5 east vs 6.0e-6 west | F: Additional energy such as shocks in the eastern nucleus | **supported**
- H: Is the eastern disk gravitationally unstable? | E: Toomre Q from kinematic model | R: Q ~ 1.5 | F: Marginally stable thanks to large dispersion | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Simple toy model to explain the main spectral features of the eastern disk, which has the simplest kinematics  
  > "we present here a simple toy model intended to explain the main features of the spectra for the eastern nuclear disk" (4 Modeling)
- Alternative: Rotation plus outflow (V_out~100 km/s) also fits acceptably but matches the IWMV curve and profiles less well  
  > "the rotation plus outflow models do not match the data as well as the rotation plus absorption models" (4.3)
- How they decided it was enough: _not stated_
- Limitation (authors): No absolute flux calibrator; flux scale uncertainty hard to quantify  
  > "This process introduces some additional uncertainty on the absolute flux scale which is difficult to quantify." (2)
- Limitation (authors): Warm-gas mass per nucleus uses global Herschel ratio  
  > "our mass estimate for the warm molecular gas for the individual nuclei should be used with caution" (footnote 5)
- Caveat (inferred, ours): Model parameters tuned by eye with no uncertainties or degeneracy exploration
- Caveat (inferred, ours): Absorber mass depends on unconstrained partition function and Tex
- Caveat (inferred, ours): Western nucleus not modeled
- Caveat (inferred, ours): Flux calibration relies on a 3C279 flux from another observation

## Reproducibility

- Data public (paper): Data cited by project code and ALMA acknowledgment  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA.00403.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Clean parameters and masks
- Missing: Self-calibration solution intervals
- Missing: Model code and tuned parameters beyond those listed
- Missing: Paper I values for L_FIR
- Data volume (inferred): ~5-20 GB raw Band 9 Cycle 0 single-track data
- Score (inferred): 3/5, Single public dataset and clear moment/mass numbers, but imaging parameters are sparse, the model is hand-tuned and relies on Paper I.
- Rediscovery candidate: no, Imaging recipe is incomplete and the kinematic model is hand-tuned without code.

## Links

- Method: Hummer & Rybicki 1968 (cite: hr68) (Line profile formalism)
- Method: van der Tak et al. 2007 (cite: tak07) (RADEX)
- Companion: Wilson et al. 2014 (cite: wilson14) (Paper I: ALMA 435 micron continuum of Arp 220)
- Related: Herschel SPIRE-FTS archival CO survey

## Checks

```json
{
 "quotes": 75,
 "quotes_ok": 75,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 80,
  "stated": 58,
  "rate": 0.725
 },
 "evidence_ok": true
}
```
