# A Cluster in the Making: ALMA Reveals the Initial Conditions for High-mass Cluster Formation

`2015ApJ...802..125R` | The Astrophysical Journal 2015 | first author: Rathborne, J. M. | arXiv: 1501.07368 | DOI: 10.1088/0004-637X/802/2/125

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, milky_way_ism
- Question: What is the small-scale gas structure and kinematics of the CMZ clump G0.253+0.016, and does it look like the initial conditions for an Arches-like high-mass cluster (smooth and centrally condensed vs hierarchical)?  
  > "Our goal is to determine the location, mass, and kinematics of the small-scale fragments within G0.253+0.016." (Introduction)
- Target **G0.253+0.016**: coordinates not stated (Table lists positions around RA 17:46:10, Dec -28:42)  
  > "Located at a distance of $\sim$8.5 kpc, G0.253+0.016  lies $\sim$100 pc from the Galactic centre (cite: Molinari11)." (Introduction); z/distance ~8.5 kpc  
  > "Located at a distance of $\sim$8.5 kpc, G0.253+0.016  lies $\sim$100 pc from the Galactic centre (cite: Molinari11)." (Introduction); distance from Molinari11  
  > "Located at a distance of $\sim$8.5 kpc, G0.253+0.016  lies $\sim$100 pc from the Galactic centre (cite: Molinari11)." (Introduction)

## Data provenance

- ALMA projects: 2011.0.00217.S
- bands: Band 3 (3 mm, 90 GHz)  
  > "Using ALMA's Band 3, the correlator was configured to use 4 spectral windows in dual polarization mode" (2 ALMA observations)
- frequencies and spectral setup: 4 spectral windows centred at 87.2, 89.1, 99.1 and 101.1 GHz, 1875 MHz bandwidth each, 488 kHz (1.4-1.7 km/s) channels; resampled to 3.4 km/s  
  > "centred at 87.2, 89.1, 99.1 and 101.1 GHz each with 1875 MHz bandwidth and 488 kHz (1.4$-$1.7 km s$^{-1}$) channel spacing" (ALMA observations); "the final data cubes were resampled to have a velocity width of 3.4 km s$^{-1}$  per channel" (ALMA observations)
- continuum bandwidth: _not stated_
- arrays: 25 antennas, Cycle 0 early science, 13-pointing mosaic  
  > "using 25 antennas as part of ALMA’s Early Science Cycle 0." (ALMA observations); "a 13-pointing mosaic was obtained to cover its full extent." (ALMA observations)
- configurations: early science 'extended configuration'  
  > "We used the ALMA early science ‘extended configuration’" (ALMA observations)
- baselines: 13-455 m  
  > "the projected baselines range from 13–455 m." (ALMA observations)
- angular resolution: ~1.7" (~0.07 pc)  
  > "The ALMA data have an angular resolution of $\sim$1.7$''$  ($\sim$0.07 pc)" (ALMA observations)
- max recoverable scale: emission insensitive above ~1.2'  
  > "the interferometric ALMA data are insensitive to emission on the largest angular scales ($>$ 1.2 $'$)" (Combination of the ALMA interferometric data with single dish data)
- sensitivity: continuum 1 sigma ~25 uJy/beam; line 1.0 mJy/beam per 3.4 km/s channel  
  > "a 1$\sigma$ continuum sensitivity of $\sim$ 25$\mu$Jy beam$^{-1}$ and line brightness sensitivity of 1.0 mJy beam$^{-1}$ per 3.4 km s$^{-1}$  channel" (ALMA observations)
- time on source: _not stated_
- observing dates: six occasions, 29 July - 1 August 2012  
  > "imaged on six different occasions over the period 29 July – 1 August 2012" (ALMA observations)
- pi or archival as stated: _not stated_
- Line: HCN v=0 J=1-0 (88.632 GHz)
- Line: HCO+ v=0 J=1-0 (89.189 GHz)
- Line: SiO v=0 J=2-1 (86.847 GHz)
- Line: HNCO 4(0,4)-3(0,3) (87.925 GHz)
- Line: NH2CHO 4(1,3)-3(1,2) (87.849 GHz)
- Other facility **Mopra (MALT90)**: single-dish zero-spacing data for HCN, HCO+, C2H, SiO, HNCO cubes  
  > "we used data from the MALT90 survey which were obtained using the Mopra 22 m telescope" (Combination of the ALMA interferometric data with single dish data)
- Other facility **Herschel**: 500 um image scaled to 3 mm as zero-spacing continuum model; dust temperatures  
  > "we scaled an image of the dust continuum emission at 500  $\mu$m  (*Herschel*, 33$''$  angular resolution) to what is expected at 3 mm" (Combination of the ALMA interferometric data with single dish data)
- Other facility **Spitzer**: 24 um image for context figure  
  > "infrared images from the *Spitzer Space Telescope*  (24 $\mu$m, $\sim$6$''$  angular resolution, shown in cyan)" (Continuum emission)
- Other facility **JCMT**: 450 um contours in context figure  
  > "Contours show single dish dust continuum emission (JCMT 450 $\mu$m , $\sim$ 7.5$''$  angular resolution)" (Continuum emission)
- External data: Dust temperature 19-27 K from Herschel 170-500 um  
  > "the dust temperature (T$_{dust}$) within G0.253+0.016  decreases smoothly from 27 K on its outer edges to 19 K in its interior (cite: Longmore12)" (Continuum emission) [from (cite: Longmore12)]
- External data: Gas temperature ~65 K  
  > "Assuming a global gas temperature for G0.253+0.016  of 65 K (cite: Ao13)" (Turbulent power spectrum) [from (cite: Ao13)]
- External data: Dust opacity kappa_1.2mm = 0.8 cm2/g with kappa ∝ nu^beta  
  > "(using $\kappa_{1.2mm}$ = 0.8 cm$^{2}$ g$^{-1}$, and $\kappa \propto \nu^{\beta}$ (cite: Chen08; Ossenkopf94),)" (Continuum emission) [from (cite: Chen08; Ossenkopf94)]
- External data: Empirical D_p to D_f conversion  
  > "(cite: Sanchez05) derive an empirical relation to convert between D$_{f}$ and D$_{p}$ (see their figure 8)" (Fractal structure) [from (cite: Sanchez05)]

## Processing

### Calibration

- pipeline or manual: Each dataset calibrated independently by ALMA support scientist, then merged; CASA and Miriad used  
  > "Each individual dataset was independently calibrated (by our ALMA support scientist) before being merged together." (ALMA observations)
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
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Single-dish data used as model during CLEAN in Fourier domain (not feathering)  
  > "was achieved using the corresponding single-dish data as a model during the CLEANing process." (Combination of the ALMA interferometric data with single dish data)
- smoothing: cubes resampled to 3.4 km/s channels  
  > "the final data cubes were resampled to have a velocity width of 3.4 km s$^{-1}$  per channel." (ALMA observations)
- final beam: ~1.7"  
  > "The ALMA data have an angular resolution of $\sim$1.7$''$" (ALMA observations)
- final rms: 25 uJy/beam continuum; 1.0 mJy/beam per channel  
  > "a 1$\sigma$ continuum sensitivity of $\sim$ 25$\mu$Jy beam$^{-1}$" (ALMA observations)

### Inherited from earlier work

- Single-dish continuum scaling details (beta assumption, Herschel 500 um)  
  > "minimising the effect of the assumption of $\beta$ (see (cite: Rathborne-pdf) for more details)" (Combination of the ALMA interferometric data with single dish data) [from (cite: Rathborne-pdf)]
- Moment definitions  
  > "using the definitions of (cite: Sault95)" (Molecular line emission) [from (cite: Sault95)]
- Perimeter-area fractal method  
  > "we employ the perimeter-area method (cite: Mandelbrot77)" (Fractal structure) [from (cite: Mandelbrot77)]
- Zero-spacing inclusion technique details  
  > "(see (cite: Ott-CASAGuide) for details)" (Combination) [from (cite: Ott-CASAGuide)]

### Not stated but needed to reproduce (our reading)

- Robust/weighting, cell size, image size, CLEAN threshold and masks
- CASA/Miriad versions and which tasks were used for each step
- Flux and bandpass/gain calibrators and flux scale uncertainty
- Continuum channel selection and line-free channels; continuum subtraction method
- Exact Mopra and Herschel data products and regridding/scaling procedure for the combination
- Power spectrum windowing/apodization, fitting ranges and break-point fitting method
- Pixel scale and contour level spacing for perimeter-area analysis
- Velocity dispersion used for virial ratios per transition

## Analysis recipe

1. **Combine ALMA with single-dish zero spacing**: Single-dish images used as model in CLEAN; Mopra MALT90 for lines, scaled Herschel 500 um for continuum  
  > "was achieved using the corresponding single-dish data as a model during the CLEANing process." (Combination)
   - software: CASA, Miriad
   - parameter: Mopra T_A* to Jy/beam factor 23 K/Jy/beam (beam 38", efficiency 0.49)  
  > "we used a scaling factor of 23 K/Jy beam$^{-1}$" (Combination)
   - parameter: Herschel 500 um scaled with flux ∝ nu^(2+beta), beta=1.2  
  > "assuming that the flux scales like $\nu ^{(2+\beta)}$, where $\beta$ was assumed to be 1.2." (Combination)
   - fitting: _not stated_
   - validation: ALMA-only recovers ~18% of 3 mm flux; compared single-dish, ALMA-only and combined images  
  > "the ALMA-only image recovers $\sim$18% of the total flux." (Combination)
2. **Convert 3 mm continuum to column density and mass**: Optically thin dust emission with single conversion factor 1.9e23 cm^-2/mJy  
  > "multiplying the measured fluxes by a single conversion factor of 1.9 $\times$10$^{23}$ ${\rm cm}^{-2}$ /mJy" (Continuum emission)
   - assumption: T_dust = 20 ± 1 K, gas-to-dust 100, kappa_3mm = 0.27 cm2/g, beta = 1.2 ± 0.1  
  > "a standard value of the gas to dust mass ratio of 100, a dust absorption coefficient ($\kappa_{3mm}$) of 0.27 cm$^{2}$ g$^{-1}$" (Continuum emission)
   - fitting: _not stated_
   - validation: T and beta uncertainties give 10% uncertainty  
  > "introduce an uncertainty of 10% for the column density, volume density, mass, and virial ratio." (Continuum emission)
3. **Moment analysis and correlation of line maps**: Moments 0, 1, 2 and peak (3-point quadratic fit) over -10 to 70 km/s; thresholds 20% of peak integrated intensity (bright lines) or 3.8 mJy/beam (~5 sigma) for faint lines; 2-D cross-correlation of image pairs  
  > "All moments were calculated over the velocity range $-$10 km s$^{-1}$ $<$V$_{LSR}$ $<$ 70 km s$^{-1}$" (Molecular line emission); "we used a threshold in the peak intensity of $>$ 3.8 mJy beam$^{-1}$  ($\sim$5$\sigma$)" (Molecular line emission)
   - fitting: _not stated_
   - validation: threshold visually checked  
  > "The choice of this threshold was visually checked" (Molecular line emission)
4. **Fractal dimension**: Perimeter-area method, P ∝ A^(Dp/2) power-law fit over contour levels; convert Dp to Df with Sanchez05  
  > "With a power-law fit of the form P $\propto$ A $^{D_{p}/2}$, we can determine the perimeter-area fractal dimension D$_{p}$." (Fractal structure)
   - fitting: linear fits to log P vs log A  
  > "With a power-law fit of the form P $\propto$ A $^{D_{p}/2}$, we can determine the perimeter-area fractal dimension D$_{p}$." (Fractal structure on small spatial scales)
   - validation: compared with SD-only image (Dp ~1.2) and simulations  
  > "find D$_{p}$ to be $\sim$1.2, consistent with its smooth distribution." (Fractal structure)
5. **Turbulent power spectrum and Jeans length**: FFT of images, annular average P(k); single power law for lines, two power laws with break for dust; compare break to Jeans length  
  > "The power spectra were generated using a Fast Fourier Transform of the images." (Turbulent power spectrum)
   - assumption: gas T=65 K, c_s=0.5 km/s, n~1e5 cm^-3  
  > "Using an average volume density for this material of $\sim$ 10$^{5}$ ${\rm cm}^{-3}$, we derive $\lambda_{J}$ to be 0.10 pc." (Turbulent power spectrum)
   - fitting: power-law fits, form not specified beyond text  
  > "we fit it with a single power law to derive $\alpha$ where, P(k) $\propto$ k$^{-\alpha}$." (Turbulent power spectrum)
   - validation: break compared with Jeans length and N-PDF core size  
  > "This value is comparable to the size scale derived from the break point in the power spectrum of the dust continuum emission" (Turbulent power spectrum)
6. **Mass, density and virial profiles**: Contours of column density give R_eff=sqrt(A/pi), mass, volume density; alpha_vir=5 sigma^2 R/GM  
  > "The virial ratio is $\alpha_{\rm vir}$, defined as $\alpha_{\rm vir}=5\sigma^2R/GM$" (Implications)
   - fitting: power-law fit to density profile  
  > "We find that the volume density profile follows very well a power law for radii $<$ 2 pc with an index of $\sim -$1.2." (Implications for the formation of young massive clusters)
   - validation: _not stated_

## Software

- **CASA** : data reduction, cleaning and imaging  
  > "All data reduction was performed using the CASA and Miriad software packages." (ALMA observations)
- **Miriad** : data reduction  
  > "All data reduction was performed using the CASA and Miriad software packages." (ALMA observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Projected fractal dimension, dust continuum (ALMA+SD) | 1.6 | not stated | dimensionless | 4 | we find a D$_{p}$ of 1.6 |
| 3D fractal dimension D_f | ~1.8 | not stated | dimensionless | 4 | we find that D$_{f}$ $\sim$ 1.8 for G0.253+0.016. |
| Dust power spectrum slope, large scales / small scales | 2.9 / 7.5 | not stated | dimensionless | 5 | the derived power-law index is $\alpha \sim$ 2.9 compared to $\alpha \sim$ 7.5 for large values of k |
| Power spectrum break scale | ~0.09 | not stated | pc | 5 | we find that the break occurs at spatial frequencies corresponding to size scales of $\sim$0.09 pc. |
| Jeans length | 0.10 | not stated | pc | 5 | we derive $\lambda_{J}$ to be 0.10 pc. |
| Mean column density (ALMA+SD) | ~8.6e22 | 10% | cm^-2 | 2 | the mean column density is $\sim$ 8.6 $\times$ 10$^{22}$ ${\rm cm}^{-2}$ |
| Volume density profile index (r<2 pc) | ~-1.2 | not stated | dimensionless | 6 | power law for radii $<$ 2 pc with an index of $\sim -$1.2 |
| Mass within 0.5 pc | ~6e3 | not stated | Msun | 6 | its total mass within a radius of 0.5 pc is only $\sim$ 6 $\times$ 10$^{3}$ M$_{\odot}$ |

## Qualitative findings

- Dust column density is best traced by molecules with higher excitation energies and critical densities; HCN and HCO+ are systematically red-shifted, indicating radial motions  
  > "the dust column density is best traced by molecules with higher excitation energies and critical densities" (Conclusions)

## Claim tuples

- H: Does turbulence shape the gas structure and is there a scale where gravity dominates? | E: Fractal dimension and power spectrum of dust continuum | R: Dp~1.6, Df~1.8; power spectrum break at ~0.09 pc, near Jeans length 0.10 pc | F: Highly fragmented, compressively turbulent structure; gravity overcomes thermal pressure below ~0.1 pc | **supported**
- H: Is the initial gas structure smooth and centrally condensed like an Arches-like cluster? | E: Mass and density profiles | R: Only ~6e3 Msun within 0.5 pc; no central concentration | F: Gas is hierarchical; cluster must become centrally condensed dynamically; smooth-initial-gas models ruled out | **supported**
- H: Which molecules trace dust column density? | E: 2-D correlation and moment comparisons | R: High-excitation molecules (e.g. NH2CHO) best correlate with dust | F: Denser interior; molecular families trace similar material | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Combining single-dish data as a CLEAN model preferred over feathering  
  > "The inclusion of the single-dish data in this manner is superior to using alternatives task such as ‘feathering’" (Combination)
- How they decided it was enough: _not stated_
- Limitation (authors): Limited velocity resolution prevents detailed virial analysis of cores  
  > "Given the limited velocity resolution of our data, a detailed analysis of the cores’ virial states are challenging with the current data." (Which molecules can be used)
- Caveat (inferred, ours): Single constant dust temperature of 20 K and fixed kappa assumed
- Caveat (inferred, ours): Zero-spacing continuum is extrapolated from Herschel with assumed beta
- Caveat (inferred, ours): Power spectrum break may be affected by beam and noise near resolution limit
- Caveat (inferred, ours): Moment thresholds affect velocity dispersions in multi-component spectra

## Reproducibility

- Data public (paper): ALMA Cycle 0 data cited by project code; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00217.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters and CASA versions
- Missing: Exact single-dish products and regridding
- Missing: Power spectrum fit details
- Data volume (inferred): ~100-300 GB raw for six Cycle 0 mosaic executions, plus MALT90 and Herschel maps
- Score (inferred): 3/5, Data are archival and the analysis is simple, but imaging and combination parameters are missing.
- Rediscovery candidate: no, Imaging, calibration and zero-spacing details are insufficient for a complete redo.

## Links

- Companion: Rathborne et al. 2014b (cite: Rathborne-pdf) (N-PDF analysis of same ALMA continuum)
- Companion: Bally et al. 2014 (cite: Bally-filaments) (HCO+ absorption filaments in same data)
- Related: MALT90
- Related: Herschel Hi-GAL

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
  "facts": 81,
  "stated": 54,
  "rate": 0.667
 },
 "evidence_ok": true
}
```
