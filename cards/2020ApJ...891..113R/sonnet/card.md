# Effect of Feedback of Massive Stars in the Fragmentation, Distribution, and Kinematics of the Gas in Two Star-forming Regions in the Carina Nebula

`2020ApJ...891..113R` | The Astrophysical Journal 2020 | first author: Rebolledo, David | arXiv: 2001.06969 | DOI: 10.3847/1538-4357/ab6d76

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, milky_way_ism
- Question: How does stellar feedback from massive stars affect fragmentation, gas distribution and kinematics in two Carina Nebula regions (Northern Cloud vs Southern Pillars)?  
  > "The science goal was to compare the internal structure of the two selected regions to investigate the effect of massive stellar feedback in the gas kinematics and distribution." (1 INTRODUCTION)
- Target **Northern Cloud (NC)**: coordinates NC1 at (l,b) ~ (287.369, -0.622) deg  
  > "the region in the NC is in the vicinity of the massive star clusters Trumpler 14 and 16 ($\sim$ 2.5 pc from nearest massive stars)" (1 INTRODUCTION); "The Carina Nebula Complex (CNC) is a spectacular star-forming region located at a distance of 2.3 kpc" (1 INTRODUCTION); z/distance 2.3 kpc  
  > "the region in the NC is in the vicinity of the massive star clusters Trumpler 14 and 16 ($\sim$ 2.5 pc from nearest massive stars)" (1 INTRODUCTION); "The Carina Nebula Complex (CNC) is a spectacular star-forming region located at a distance of 2.3 kpc" (1 INTRODUCTION); distance from Smith & Brooks 2008  
  > "the region in the NC is in the vicinity of the massive star clusters Trumpler 14 and 16 ($\sim$ 2.5 pc from nearest massive stars)" (1 INTRODUCTION); "The Carina Nebula Complex (CNC) is a spectacular star-forming region located at a distance of 2.3 kpc" (1 INTRODUCTION)
- Target **Southern Pillars (SP)**: coordinates _not stated_; z/distance 2.3 kpc  
  > "the region in the SP is located much further away ($\sim$ 30 pc) from the center of the radiation field." (1 INTRODUCTION); distance from Smith & Brooks 2008  
  > "the region in the SP is located much further away ($\sim$ 30 pc) from the center of the radiation field." (1 INTRODUCTION)

## Data provenance

- ALMA projects: 2016.1.01609.S
- bands: Band 3  
  > "Four spectral basebands in Band 3 are utilized to observe twelve spectral lines and the continuum." (2.1 ALMA observations)
- frequencies and spectral setup: 12 lines, 58.6 MHz windows; channel 61 kHz for HCN, HCO+, H13CN, H13CO+, 122 kHz others  
  > "For the main lines HCN, HCO$^{+}$, H$^{13}$CN and H$^{13}$CO$^{+}$, the channel resolution was 61 kHz. For the remaining lines, the channel resolution was 122 kHz." (2.1 ALMA observations)
- continuum bandwidth: 2000 MHz centered at 99.5 GHz  
  > "The continuum window was centered in 99.5 GHz, and its bandwidth was chosen to be 2000 MHz in order to maximize sensitivity." (2.1 ALMA observations)
- arrays: 12 m and 7 m arrays  
  > "12 m and 7 m array observations are requested to maximize flux recovery at scales $\sim 1\ensuremath{'}$" (2.1 ALMA observations)
- configurations: mosaic of 134 pointings (12 m) and 46 pointings (7 m) per region  
  > "The mosaic for the 12 m array was composed of 134 pointings, while 46 pointings were needed to cover the same area with the 7 m array." (2.1 ALMA observations)
- baselines: _not stated_
- angular resolution: ~2.8"x1.8" beam (3" requested)  
  > "is $\sim 2.8\ensuremath{''}\times1.8\ensuremath{''}$ using a robust weighting of 0.5" (2.2 Imaging)
- max recoverable scale: _not stated_
- sensitivity: 10 mJy/beam per channel; continuum 0.22 mJy/beam (NC), 0.12 mJy/beam (SP)  
  > "The noise in a single channel is 10 mJy/beam. For the continuum maps, the achieved noise is 0.22 mJy/beam for the NC, and 0.12 mJy/beam for the SP for the 2 GHz window." (2.2 Imaging)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: HCN v=0 J=1-0, F=2-1 (88.63184 GHz)
- Line: HCO+ J=1-0 (89.18852 GHz)
- Line: H13CO+ J=1-0 (86.75428 GHz)
- Line: SiO v=0 J=2-1 (86.84696 GHz)
- Other facility **APEX/ATLASGAL**: 870 um dust maps used to recover diffuse emission and for densities  
  > "To correct for the missing flux, in this study we have used APEX data from the ATLASGAL survey." (4.6 Distribution of column densities)
- Other facility **Herschel**: gas column density map (via Rebolledo 2016) for total mass  
  > "using the gas column density map derived in (cite: 2016MNRAS.456.2406R) from Herschel maps" (4.2 Fraction of the mass in cores)
- External data: Dust temperatures 23 K (SP) and 28 K (NC)  
  > "assuming dust temperature values of 23 K for the SP and 28 K for the NC, both reported in (cite: 2016MNRAS.456.2406R)" (4.1 Masses of the cores) [from (cite: 2016MNRAS.456.2406R)]
- External data: Herschel gas column density map  
  > "using the gas column density map derived in (cite: 2016MNRAS.456.2406R) from Herschel maps" (4.2 Fraction of the mass in cores) [from (cite: 2016MNRAS.456.2406R)]

## Processing

### Calibration

- pipeline or manual: raw data downloaded and calibrated data regenerated  
  > "We downloaded the raw data from the ALMA archive and regenerated the calibrated data for both arrays." (2.2 Imaging)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA tclean, 12 m + 7 m combined  
  > "the 12 m and 7 m array observations were combined and imaged together using the *tclean* task of the CASA package" (2.2 Imaging)
- deconvolver: _not stated_
- weighting robust: robust = 0.5  
  > "using a robust weighting of 0.5" (2.2 Imaging)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: joint imaging of 12m+7m; ALMA+ATLASGAL feathered with Miriad immerge for N-PDF  
  > "we have used the miriad task *immerge* which is a linear method, also known as feathering" (4.6 Distribution of column densities)
- smoothing: _not stated_
- final beam: ~2.8"x1.8"  
  > "is $\sim 2.8\ensuremath{''}\times1.8\ensuremath{''}$ using a robust weighting of 0.5" (2.2 Imaging)
- final rms: 0.22 mJy/beam NC, 0.12 mJy/beam SP continuum  
  > "the achieved noise is 0.22 mJy/beam for the NC, and 0.12 mJy/beam for the SP for the 2 GHz window" (2.2 Imaging)

### Inherited from earlier work

- Log-normal N-PDF fitting approach  
  > "Following the same approach detailed in (cite: 2016MNRAS.456.2406R), we have fitted a log-normal function to the N-PDFs" (4.6 Distribution of column densities) [from (cite: 2016MNRAS.456.2406R)]
- Core size definition  
  > "The sizes were calculated following (cite: 1987ApJ...319..730S) and (cite: 2006PASP..118..590R)." (4.1 Masses of the cores) [from (cite: 1987ApJ...319..730S); (cite: 2006PASP..118..590R)]
- Bayesian linear regression for size-linewidth  
  > "Following (cite: 2007ApJ...665.1489K), the fitting is performed as follows," (4.5.2 PCA) [from (cite: 2007ApJ...665.1489K)]

### Not stated but needed to reproduce (our reading)

- Line-free channels and continuum subtraction method for line cubes
- CASA version and tclean deconvolver/threshold/masking, cell and image size
- Flux calibrator and calibration details
- MCMC sampler and priors for Kelly regression
- Method for spectra Gaussian fit and PCA parameters in TurbuStat
- N-PDF binning and ALMA-ATLASGAL feathering parameters
- Dendrogram input cube smoothing and velocity-dispersion definition per leaf
- Core-mass equation and how free-free was handled in masses

## Analysis recipe

1. **Image 12m+7m data**: Combined imaging of both arrays with tclean  
  > "the 12 m and 7 m array observations were combined and imaged together using the *tclean* task of the CASA package" (2.2 Imaging)
   - software: CASA
   - parameter: robust 0.5; channel width 0.41 km/s for main lines  
  > "For the main lines, HCN, HCO$^{+}$, H$^{13}$CN and H$^{13}$CO$^{+}$, the channel width is 0.41 $\mbox{km s$^{-1}$}$." (2.2 Imaging)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure core fluxes and sizes**: 2D Gaussian plus offset fitted to each core  
  > "a 2D gaussian and a flux offset level have been fitted to each core using the task *imfit* from the Multichannel Image Reconstruction (Miriad) package" (3.1.1 Continuum)
   - software: Miriad
   - parameter: cores kept only if S/N > 10 in NC  
  > "for the NC we have decided to keep only the three compact sources with obvious round shape and high S/N ratio ($>10$)" (3.1.1 Continuum)
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive core masses**: Dust continuum mass with fixed temperature and opacity  
  > "We used a dust opacity $\kappa_\mathrm{3mm}=0.186$ cm$^{2}$ gr$^{-1}$ computed from extrapolation of $\kappa_\mathrm{1.3mm}=1$ cm$^{2}$ gr$^{-1}$, and assuming $\beta =2$." (4.1 Masses of the cores)
   - assumption: T = 23 K (SP), 28 K (NC); gas-to-dust 100; beta=2; d=2.3 kpc  
  > "A Gas-to-Dust ratio of 100 was assumed." (4.1 Masses of the cores)
   - fitting: _not stated_
   - validation: _not stated_
4. **Core velocity dispersion and virial parameter**: Gaussian fit to H13CO+ core spectra; alpha_vir = 5 dv^2 R/(G M)  
  > "The velocity dispersion is calculated by fitting a gaussian function to the spectral profiles derived for each core." (4.3 Internal dynamics of the cores)
   - assumption: uniform density, no magnetic fields or external pressure  
  > "ignoring magnetic fields and external pressures, and assuming a uniform density profile" (4.3 Internal dynamics of the cores)
   - fitting: _not stated_
   - validation: _not stated_
5. **Jeans analysis**: Jeans mass from ATLASGAL-derived density in 20" radius sphere and dust temperature  
  > "the volume density is estimated assuming a spherical shape of $20\mbox{$\ensuremath{''}$ }$ radius" (4.4 Gas fragmentation)
   - assumption: kappa_0.87mm=0.42, beta=2, gas-to-dust 100  
  > "A Gas-to-Dust ratio of 100 is used." (4.4 Gas fragmentation)
   - fitting: _not stated_
   - validation: grid of Jeans mass over n and T explored  
  > "Figure [12](#MJ_density) shows a grid of Jeans mass values for a given range of $n_\mathrm{H2}$ and temperatures." (4.4 Gas fragmentation)
6. **Turbulence via dendrograms**: SCIMES dendrograms on HCO+ and H13CO+ cubes; K-S and t-tests on leaf velocity dispersions  
  > "The decomposition was performed using minvalue $=5\sigma$, mindelta$=2 \sigma$, and minpix equal to the number of pixels inside an area of 3 synthesized beams." (4.5.1 Dendrograms)
   - software: SCIMES, Astropy
   - fitting: _not stated_
   - validation: _not stated_
7. **Turbulence via PCA**: PCA on HCO+ cubes giving size-linewidth; Bayesian MCMC regression for alpha  
  > "For each scaling relation in the SP and NC, we have run $2 \times 10^{4}$ random draws to sample the probability distribution of the fit parameters." (4.5.2 PCA)
   - software: TurbuStat
   - fitting: _not stated_
   - validation: _not stated_
8. **N-PDF**: Feather ALMA with ATLASGAL (immerge), build N-PDF, fit log-normal, infer Mach number  
  > "The fit was conducted only using the bins in the range $N_\mathrm{H2,sen} < N_\mathrm{H2} < N_\mathrm{H2,log}$" (4.6 Distribution of column densities)
   - software: Miriad
   - assumption: _not stated_
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : calibration regeneration and tclean imaging  
  > "imaged together using the *tclean* task of the CASA package" (2.2 Imaging)
- **Miriad** : imfit core fitting and immerge feathering  
  > "using the task *imfit* from the Multichannel Image Reconstruction (Miriad) package" (3.1.1 Continuum)
- **SCIMES** : dendrogram decomposition  
  > "we made use of SCIMES, a Python package to find relevant structures into dendrograms of molecular gas emission" (4.5.1 Dendrograms)
- **TurbuStat** : PCA algorithm  
  > "we use the algorithm implemented in the TurbuStat python package" (4.5.2 PCA)
- **Astropy** : used by SCIMES  
  > "SCIMES makes use of Astropy" (4.5.1 Dendrograms)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| NC1 continuum flux | 14.40 | 0.92 | mJy | 2 | / NC1                 / 14.40 $\pm$ 0.92    / 2.33                       / 1.23                       / |
| mean core mass NC | 19.4 | not stated | Msun | 3 | While the NC has a mean core mass of 19.4 $\mbox{$M_{\odot}$}$, the mean in the SP is 3.8 $\mbox{$M_{\odot}$}$ |
| mean core mass SP | 3.8 | not stated | Msun | 3 | the mean in the SP is 3.8 $\mbox{$M_{\odot}$}$ |
| Jeans mass | ~4.5 (both regions) | not stated | Msun | 5 | we estimated $M_\mathrm{J} \sim 4.5\ \mbox{$M_{\odot}$}$ for both regions |
| mean HCO+ leaf velocity dispersion NC / SP | 0.37 / 0.31 | not stated | km/s | 6 | The mean velocity dispersion is 0.37 $\mbox{km s$^{-1}$}$ for the NC, white for the SP is 0.31 $\mbox{km s$^{-1}$}$. |
| PCA alpha NC | 0.59 | 90% HDI [0.37,0.75] | dimensionless | 7 | the peak value is 0.59 and a 90% HDI of \[0.37,0.75\] in the NC |
| PCA alpha SP | 0.34 | 90% HDI [0.01,0.52] | dimensionless | 7 | peak at 0.34 for the SP, with a 90% HDI of \[0.01,0.52\] |
| N-PDF transition column density NC / SP | 3.2e23 / 1.7e23 | not stated | cm^-2 | 8 | In the NC, the $N_\mathrm{H2,log}$ is $\sim 3.2\times 10^{23}\ \mathrm{cm}^{-2}$, while in the SP the $N_\mathrm{H2,log}$ is $\sim 1.7\times 10^{23}\ \mathrm{cm}^{-2}$ |
| log-normal width delta_H2 NC / SP | 0.62 / 0.39 | not stated | dimensionless | 8 | Table [\[log-normal-fit\]](#log-normal-fit) shows a value of $\delta_\mathrm{H2}=0.62$ for the NC. In contrast, for the SP $\delta_\mathrm{H2}=0.39$. |
| Mach number NC / SP | 1.37 / 0.81 | not stated | dimensionless | 8 | This imply a $\mathcal{M}=1.37$ for the NC and $\mathcal{M}=0.81$ for the SP |

## Qualitative findings

- Diffuse SiO follows PDR/shock fronts in NC but is absent in SP  
  > "In contrast to the NC, in the SP diffuse SiO is not seen." (3.1.2 SiO)

## Claim tuples

- H: Stellar feedback affects core fragmentation | E: Compare continuum cores in NC and SP | R: 3 cores of mean 19.4 Msun in NC vs 10 cores of mean 3.8 Msun in SP | F: fewer, more massive cores where feedback is stronger | **supported**
- H: Thermal Jeans fragmentation explains core masses | E: Compare Jeans mass ~4.5 Msun to core masses | R: consistent in SP, factor 4-5 smaller than NC cores | F: SP thermal; NC may need turbulent fragmentation | **partially**
- H: Turbulence is higher in NC | E: Dendrograms and PCA on HCO+, H13CO+ | R: HCO+ dispersions differ significantly; PCA alpha overlaps | F: higher turbulence in NC, only in low-density gas | **partially**
- H: N-PDF width reflects turbulence | E: Log-normal fit to ALMA+ATLASGAL N-PDFs | R: wider in NC (0.62 vs 0.39) | F: supports higher turbulence in NC | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): N-PDFs affected by sensitivity limit, extrapolation of ATLASGAL to 3 mm, and free-free contamination  
  > "Thus, our N-PDFs are probably affected by our sensitivity limit, more strongly at the low column density side of the distribution." (4.6 Distribution of column densities)
- Caveat (inferred, ours): Only 3 cores in NC; small-number statistics
- Caveat (inferred, ours): Free-free contamination biases NC core masses
- Caveat (inferred, ours): Single temperature per region assumed
- Caveat (inferred, ours): Core count difference may reflect S/N>10 selection applied only in NC

## Reproducibility

- Data public (paper): Raw data downloaded from ALMA archive  
  > "We downloaded the raw data from the ALMA archive and regenerated the calibrated data for both arrays." (2.2 Imaging)
- Products in archive: _not stated_
- Missing: CASA version and tclean parameters
- Missing: line-free channels
- Missing: MCMC and PCA settings
- Missing: N-PDF binning
- Data volume (inferred): ~100-300 GB raw
- Score (inferred): 3/5, Public data and many steps described, but key imaging and fitting parameters missing.
- Rediscovery candidate: yes, Public data, numeric results (core fluxes, masses, N-PDF), moderately complete recipe.

## Links

- Method: (cite: 2007ApJ...665.1489K) (Bayesian linear regression)
- Method: (cite: 2002ApJ...566..276B) (PCA alpha-eta relation)
- Companion: (cite: 2016MNRAS.456.2406R) (Herschel/Mopra CNC maps, temperatures, N-PDF approach)
- Companion: (cite: 2019MNRAS.483.1437C) (Mopra dense-gas survey of CNC clumps)
- Related: ATLASGAL
- Related: Mopra CNC survey

## Checks

```json
{
 "quotes": 71,
 "quotes_ok": 71,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 90,
  "stated": 48,
  "rate": 0.533
 },
 "evidence_ok": true
}
```
