# Dynamics of a massive binary at birth

`2019NatAs...3..517Z` | Nature Astronomy 2019 | first author: Zhang, Yichen | arXiv: 1903.07532 | DOI: 10.1038/s41550-019-0718-y

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: Is the massive protostar IRAS07299-1651 a binary at birth, what are its orbital dynamics and masses, and does this support disk fragmentation as the formation mechanism?  
  > "Little is known about binarity during formation stages." (abstract)
- Target **IRAS07299-1651**: coordinates Source A: 7h32m09.786s, -16d58m12.146s; Source B: 7h32m09.793s, -16d58m12.196s (J2000)  
  > "We observed infrared source IRAS07299-1651, thought to be a massive protostar(cite: Debuizer17), $1.68\:$kpc away(cite: Reid09)" (main text); z/distance 1.68 kpc  
  > "We observed infrared source IRAS07299-1651, thought to be a massive protostar(cite: Debuizer17), $1.68\:$kpc away(cite: Reid09)" (main text); distance from Reid09  
  > "We observed infrared source IRAS07299-1651, thought to be a massive protostar(cite: Debuizer17), $1.68\:$kpc away(cite: Reid09)" (main text)

## Data provenance

- ALMA projects: 2015.1.01454.S, 2016.1.00125.S
- bands: Band 6 (1.3 mm)  
  > "The observations were carried out with ALMA in Band 6 on April 3, 2016 with the C36-3 configuration" (Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: 2 GHz spectral window  
  > "A spectral window with a bandwidth of 2 GHz was used to map the 1.3 mm continuum." (Observations)
- arrays: _not stated_
- configurations: C36-3, C36-6, C40-9  
  > "on Sept. 17, 2016 with the C36-6 configuration, and on Sept, 23, 2017 with the C40-9 configuration" (Observations)
- baselines: 15 m-462 m (C36-3), 15 m-3.2 km (C36-6), 41 m-12 km (C40-9)  
  > "40 antennas were used and the baselines range from 41 m to 12 km in the C40-9 configuration" (Observations)
- angular resolution: 35 mas x 29 mas (high-res continuum); 0.22'' x 0.15'' (low-res)  
  > "The resultant synthesized beams are $0.035'' \times
0.029''$ for the high resolution continuum data" (Observations)
- max recoverable scale: about 11'' (low-res) and 3.9'' (high-res)  
  > "The largest recoverable scales of the low- and high-resolution data are about 11$''$ and 3.9$''$, respectively." (Observations)
- sensitivity: _not stated_
- time on source: 3, 6, and 18 min in the three configurations  
  > "The total integration time is 3, 6, and 18 min in the three configurations." (Observations)
- observing dates: 2016-04-03, 2016-09-17, 2017-09-23  
  > "on April 3, 2016 with the C36-3 configuration, on Sept. 17, 2016" (Observations)
- pi or archival as stated: _not stated_
- Line: H30alpha H30alpha recombination line (not stated)
- Line: CH3OH 4(2,2)-3(1,2) (not stated)
- External data: Distance 1.68 kpc  
  > "$1.68\:$kpc away(cite: Reid09)" (main text) [from Reid09]
- External data: Total bolometric luminosity (1-4)x10^4 Lsun  
  > "consistent with the $(1-4)\times10^4\:L_\odot$ estimate for the total bolometric luminosity of this system(cite: Debuizer17)" (Estimating protostellar masses from free-free emission) [from Debuizer17]
- External data: Dust opacity 0.00899 cm2/g at 1.3 mm incl. gas-to-dust 100  
  > "an opacity of $\kappa_\mathrm{1.3mm}=0.00899~\mathrm{cm}^2~\mathrm{g}^{-1}$ with a standard gas-to-dust mass ratio of 100 included (ref. (cite: Ossenkopf94))" (Estimating ambient gas mass) [from Ossenkopf94]
- Simulation/model as data: Protostellar evolution models give mass ranges 8-19 Msun (A) and 7-17 Msun (B) from ionizing photon rates  
  > "such ionizing photon rates correspond to protostellar mass ranges of $8-19~M_\odot$ for Source A, and $7-17~M_\odot$ for Source B" (Estimating protostellar masses from free-free emission)

## Processing

### Calibration

- pipeline or manual: calibrated in CASA; details not given  
  > "The data were calibrated and imaged in CASA(cite: McMullin07)." (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0750+1231 (bandpass and flux)  
  > "J0750+1231 was used for bandpass and flux calibration" (Observations)
- flux scale uncertainty: _not stated_
- self calibration: applied to continuum and line data, separately for each of three configurations  
  > "The self-calibration was performed for the data of three configurations separately." (Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: robust = 0.5  
  > "using robust weighting with the robust parameter of 0.5" (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: C36-3 and C36-6 combined (low-res); C40-9 not combined  
  > "The data from C36-3 and C36-6 configurations were combined (referred to as “low-resolution” data)" (Observations)
- smoothing: _not stated_
- final beam: 0.035''x0.029'' high-res continuum; 0.035''x0.030'' H30a; 0.22''x0.15'' low-res continuum; 0.25''x0.17'' CH3OH  
  > "$0.22'' \times
0.15''$ for the low resolution continuum data, and $0.25'' \times
0.17''$ for the low-resolution CH$_3$OH data" (Observations)
- final rms: _not stated_

### Inherited from earlier work

- Free-free mass estimation follows spherical uniform-density ionized region method  
  > "We follow the method of ref. (cite: Schmiedeke16), which assumes a spherical ionized region with a uniform electron density." (Estimating protostellar masses from free-free emission) [from Schmiedeke16]
- Centroid position uncertainty formulae  
  > "described by the following relation(cite: Zhang17; Condon97) $\Delta \theta_\mathrm{fit}=\theta_\mathrm{beam}/(2~\mathrm{S/N})$" (Determining the H30alpha emission centroids) [from Zhang17; Condon97]
- Rotating-infall model for large-scale structure  
  > "We use a model of rotating-infall(cite: Sakai14) to explain the kinematic features" (main text) [from Sakai14]

### Not stated but needed to reproduce (our reading)

- Self-calibration solution intervals and number of iterations
- CASA version and calibration procedure
- Clean masks, thresholds, cell and image sizes
- Line-free channels for continuum subtraction
- Spectral window frequencies
- Fitting parameter ranges and optimiser for ring model
- Which ALMA project corresponds to which configuration

## Analysis recipe

1. **Image continuum and H30a**: CLEAN imaging with robust 0.5 after self-calibration; source positions with imfit  
  > "The CLEAN algorithm was used to image the data, using robust weighting with the robust parameter of 0.5." (Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure H30a central velocities**: Gaussian fits to spectra at continuum peaks; uncertainties by Monte Carlo noise and sinusoidal perturbation for asymmetry  
  > "We fit the H30$\alpha$ spectra at the continuum peak positions of the two sources with Gaussian profiles to determine the central velocities." (Estimating the line-of-sight velocities)
   - assumption: H30a central velocities trace protostar radial velocities  
  > "We assume that the measured H30$\alpha$ central velocities are a good measure of the true source velocities." (Estimating the line-of-sight velocities)
   - fitting: Gaussian profile fit  
  > "We fit the H30$\alpha$ spectra at the continuum peak positions of the two sources with Gaussian profiles to determine the central velocities." (Estimating the line-of-sight velocities of the protostars.)
   - validation: fits to line wings only and to the overall spectrum give 14.5 km/s  
  > "the fitted central velocities are both $14.5~\mbox{km s}^{-1}$" (Estimating the line-of-sight velocities)
3. **Derive orbital constraints and mass ratio**: Circular and elliptical orbit limits from apparent separation and velocity difference; mass ratio from center-of-mass velocity  
  > "For an elliptical orbit with eccentricity $e$, the minimum system mass is $M_\mathrm{min}=M_0/(1+e)$." (main text)
   - assumption: Center-of-mass velocity equals cloud systemic velocity 16.5-18 km/s  
  > "Assuming the center of mass radial velocity of the binary is the same as the molecular cloud systemic velocity" (main text)
   - fitting: _not stated_
   - validation: _not stated_
4. **Separate free-free and dust continuum and estimate protostar masses**: Line-to-continuum ratio under LTE optically thin assumption; ionizing photon rates to ZAMS and protostellar evolution masses  
  > "we first use the observed continuum-subtracted intensity of the H30$\alpha$ HRL to estimate the level of free-free continuum emission" (Estimating contributions of free-free emission)
   - parameter: Te = 8000 K, N(He+)/N(H+)=0.08  
  > "Assuming a typical ionized gas temperature of $T_\mathrm{e}=8000~\mbox{K}$" (Estimating contributions of free-free emission)
   - fitting: _not stated_
   - validation: optical depths checked: tau_ff<0.13, tau_H30a=0.25 for A  
  > "Therefore the optically thin assumptions are indeed reasonably valid." (Estimating contributions of free-free emission)
5. **Fit rotating ring to H30a centroids**: Per-channel 2D Gaussian centroids (>20 sigma) fit with half-ring model, chi2 minimisation  
  > "The best-fit model was obtained by varying the input parameters within reasonable ranges, and minimizing the value of" (Model fitting of the H30alpha centroids)
   - parameter: weights w_pos=0.9, w_int=0.1; thermal broadening FWHM 19 km/s  
  > "we use weights of $w_\mathrm{pos}=0.9$ and $w_\mathrm{int}=0.1$ in the fitting." (Model fitting of the H30alpha centroids)
   - assumption: Keplerian rotation; only half of ring emits  
  > "In the model, we assume only half of the ring is emitting H30$\alpha$ emission." (Model fitting of the H30alpha centroids)
   - fitting: chi2 minimisation; uncertainties from parameter range with chi2<=3 others fixed  
  > "The uncertainty of each parameter is estimated using the parameter range of models with $\chi^2\leq 3$ while keeping other parameters unchanged." (Model fitting of the H30alpha centroids)
   - validation: _not stated_
6. **Model large-scale infall and estimate gas masses**: Rotating-infall parabola model to CH3OH PV diagram; optically thin dust mass for extended emission  
  > "In this model, the material is infalling and rotating with angular momentum conserved." (Supplementary Information)
   - parameter: Tdust 50-100 K, kappa1.3mm=0.00899 cm2/g, D=1680 pc  
  > "For $T_\mathrm{dust}=50-100~\mbox{K}$" (Estimating ambient gas mass)
   - fitting: by-eye model, r0=0.5'', V_sys=15, v0=7.5 km/s  
  > "In the model, $r_0=0.5''$ (840 au), $V_\mathrm{sys}=15~\mbox{km s}^{-1}$, $v_0=7.5~\mbox{km s}^{-1}$." (Supplementary Information)
   - validation: _not stated_

## Software

- **CASA** : calibration, self-calibration, CLEAN imaging, imfit  
  > "The data were calibrated and imaged in CASA(cite: McMullin07)." (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| H30a velocity Source A | 15.5 | 1.1 | km/s | 2 | $15.5\pm1.1\:\mbox{km s}^{-1}$ for A |
| H30a velocity Source B | 25.0 | 1.6 | km/s | 2 | $25.0\pm1.6\:\mbox{km s}^{-1}$ for B |
| minimum total system mass M0 | 18.4 | 7.4 | Msun | 3 | $M_0=18.4\pm7.4\:M_\odot$ |
| maximum orbital period | 570 | 120 | yr | 3 | $P_0=(5.7\pm1.2)\times 10^2$ years |
| free-free flux A / B at 1.3 mm | 39 / 4 | not stated | mJy | 4 | We estimate free-free components in the 1.3 mm continuum to be 39 mJy and 4 mJy in Sources A and B |
| ring radius | 7 | 1 | mas | 5 | $R_\mathrm{ring}=7\pm1\:\mathrm{mas}$ |
| ring rotation velocity | 21 | 2 | km/s | 5 | $V_\mathrm{rot}=21\pm2\:\mbox{km s}^{-1}$ |
| dynamical mass of Source A | 6 | 2 | Msun | 5 | corresponding to a central mass of $6\pm2\:M_\odot$ |
| infall model central mass | 27 | 6 | Msun | 6 | This model requires a central mass of $27\pm6~M_\odot$ |
| ambient gas mass >500 au | 3.8-8 | not stated | Msun | 6 | the mass of this ambient gas is estimated to be $3.8-8~M_\odot$ |

## Qualitative findings

- H30a emission from A is consistent with rotation along an inclined ring; only the far-side half is seen, likely blocked by an opaque dusty disk.  
  > "This can naturally explain why only the eastern half of the ring, which is the far side, is seen in H30$\alpha$ emission." (main text)

## Claim tuples

- H: IRAS07299-1651 hosts a bound massive protobinary | E: 1.3 mm continuum and H30a at 35 mas resolution | R: Two sources 180 au apart with 9.5 km/s velocity difference | F: Minimum total mass 18 Msun, consistent with free-free-derived masses | **supported**
- H: Individual protostars have small feeding disks | E: Centroid analysis and ring fit of H30a around Source A | R: Ring radius 12 au, Vrot 21 km/s, 6 Msun | F: Rotating ionized structure at 12 au scale | **supported**
- H: The binary formed by disk fragmentation | E: Compare infall, mass ratio, source multiplicity with models | R: Infall structures, centrifugal barrier 840 au, few other sources, mass ratio ~0.7-0.8 | F: Results favour disk fragmentation, with a caveat of orbital/disk misalignment >54 deg | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Turbulent fragmentation judged unlikely given near-equal masses and lack of nearby sources  
  > "Production of near equal mass high-mass stars by turbulent fragmentation, i.e., independent formation events that happen to form near each other in a bound state, is unlikely" (main text)
- How they decided it was enough: _not stated_
- Limitation (authors): Free-free/dust separation uncertain without other continuum frequencies  
  > "Without additional observations of the continuum emission at other frequencies, it is difficult to separate the components of the free-free emission and dust continuum emission more accurately." (Estimating contributions of free-free emission)
- Limitation (authors): Ring model is illustrative; other parameters less robust  
  > "Other parameters estimated from this model fitting are less robust." (Model fitting of the H30alpha emission centroids)
- Caveat (inferred, ours): Assumes H30a velocity traces stellar velocity despite known offsets
- Caveat (inferred, ours): Mass ratio and orbit depend on assumed cloud velocity
- Caveat (inferred, ours): Single-epoch data cannot show orbital motion
- Caveat (inferred, ours): Free-free fraction depends on assumed Te

## Reproducibility

- Data public (paper): Project codes listed; derived data on request  
  > "The data that support the plots within this paper and other findings of this study are available from the corresponding author upon reasonable request." (Data avalability)
- Products in archive: _not stated_
- Missing: Self-cal parameters
- Missing: CASA version
- Missing: Fit parameter ranges and code for ring model
- Missing: Image sizes and masks
- Data volume (inferred): ~50-200 GB raw across three configurations
- Score (inferred): 3/5, Public data and quantitative recipe, but processing details and custom model codes are unspecified.
- Rediscovery candidate: yes, Data public and central numbers (velocities, fluxes, masses) are measurable, though ring model needs reimplementation.

## Links

- Method: Schmiedeke16 (free-free emission modelling)
- Method: Sakai14 (rotating-infall model)
- Related: SOMA survey

## Checks

```json
{
 "quotes": 66,
 "quotes_ok": 66,
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
  "facts": 79,
  "stated": 48,
  "rate": 0.608
 },
 "evidence_ok": true
}
```
