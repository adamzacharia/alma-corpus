# The Excitation Conditions of CN in TW Hya

`2020ApJ...899..157T` | The Astrophysical Journal 2020 | first author: Teague, Richard | arXiv: 2007.11906 | DOI: 10.3847/1538-4357/aba956

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: Is CN emission in the TW Hya disk in LTE, and what excitation temperatures, kinetic temperatures and densities, and hence emitting regions, does it trace across the N=1-0, 2-1 and 3-2 transitions?  
  > "In this paper we present a combined analysis of three transitions of CN, $N=3-2$, $N=2-1$ and $N=1-0$ in TW Hya, the closest planet-forming disk at 60.1 pc" (Introduction)
- Target **TW Hya**: coordinates _not stated_; z/distance 60.1 pc  
  > "the closest planet-forming disk at 60.1 pc (cite: Bailer-Jones_ea_2018)" (Introduction); distance from Bailer-Jones et al. 2018 (Gaia)  
  > "the closest planet-forming disk at 60.1 pc (cite: Bailer-Jones_ea_2018)" (Introduction)

## Data provenance

- ALMA projects: 2013.1.00387.S, 2017.1.01199.S, 2016.1.00440.S
- bands: Band 3, 6 and 7 (N=1-0, 2-1, 3-2 at 113.5, 226.8, 340.1 GHz)  
  > "We combine ALMA Band 3, 6 and 7 observations spanning the the $N=1-0$, $N=2-1$ and $N=3-2$ transitions at 113.5 GHz, 226.8 GHz and 340.1 GHz, respectively." (2 Observations)
- frequencies and spectral setup: Channel widths: Band 3 31 kHz (80 m/s); Band 6 30 kHz (40 m/s); Band 7 244 kHz (215 m/s)  
  > "at a 31 kHz ($80~{\rm m\,s^{-1}}$) spectral resolution" (2.1 Band 3); "at a channel spacing of 30 kHz ($40~{\rm m\,s^{-1}}$)" (2.1 Band 6); "with a channel spacing of 244 kHz ($215~{\rm m\,s}^{-1}$)" (2.1 Band 7)
- continuum bandwidth: _not stated_
- arrays: Band 3: 42 antennas; Band 6: 34 antennas; Band 7: 45 antennas  
  > "using 34 antennae" (2.1 Band 6)
- configurations: _not stated_
- baselines: Band 3: 15-1261 m; Band 6: up to 550 m; Band 7: 15-700 m  
  > "used 42 antennas spanning baselines from 15 m to 1261 m" (2.1 Band 3); "With baselines only extending to 550 m, these observations were the most compact of the three." (2.1 Band 6); "Baselines ranged between 15 and 700 m" (2.1 Band 7)
- angular resolution: Band 3 0.54"x0.48"; Band 6 0.52"x0.43"; Band 7 0.31"x0.29"  
  > "a robust value of 0 was chosen yielding a beam of $0.54\ensuremath{''} \times 0.48\ensuremath{''}$ at a position angle of 46.1$^\circ$" (2.2 Imaging)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: Band 3: 78 min; Band 6: 46 min; Band 7: 48 min  
  > "included 39 minutes of on-source integration, totaling 78 minutes on source" (2.1 Band 3); "integrated on source for 46 minutes" (2.1 Band 6); "with a total on-source time of 48 minutes" (2.1 Band 7)
- observing dates: Band 3: 2018 Sep 15 and 16; Band 6: 2015 May 13; Band 7: 2016 Dec 2  
  > "were taken the two consecutive nights, September 15 and 16, 2018" (2.1 Band 3); "Observations were performed on May 13, 2015" (2.1 Band 6); "were taken December 2, 2016" (2.1 Band 7)
- pi or archival as stated: Band 6 previously published (Teague+2016); Bands 3 and 7 unpublished before this work  
  > "have not been previously published" (2 Observations)
- Line: CN N=1-0 (J=3/2-1/2, 1/2-1/2 groups) (113.488-113.520 GHz)
- Line: CN N=2-1 (226.659-226.892 GHz)
- Line: CN N=3-2 (339.447-340.265 GHz)
- External data: CN line frequencies, Einstein A, degeneracies, dipole strengths  
  > "The line frequencies, Einstein A coefficients, upper state degeneracies and dipole strengths were taken from the CDMS" (Table 1 notes) [from CDMS (cite: CDMS)]
- External data: CN-H2 collisional rates including hyperfine structure, from LAMDA  
  > "with the latest CN collisional rates which include hyperfine structure (cite: Kalugina_Lique_2015), obtained from the LAMDA database" (4.1 Non-LTE Excitation) [from Kalugina & Lique 2015; Schoeier et al. 2005]
- External data: TW Hya physical structure model for densities and temperatures  
  > "Based on the physical structure model from (cite: Qi_ea_2013), this is achieved at heights of $z\,/\,r \gtrsim 0.2$." (4.1 Non-LTE Excitation) [from Qi et al. 2013]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Band 3: J1107-4449 (bandpass and flux)  
  > "J1107-4449 was used for all three executions as bandpass and flux calibrator" (2.1 Band 3)
- flux scale uncertainty: 5% Band 3, 10% Bands 6 and 7  
  > "the flux calibration uncertainties of 5% in Band 3 and 10% for Band 6 and 7" (3.1 Excitation Temperature)
- self calibration: Phase self-cal with 30 s final solution interval in all bands (Band 3: three rounds)  
  > "The data were iteratively phase self-calibrated for three rounds with a final solution interval of 30 s." (2.1 Band 3); "Data were self-calibrated using a solution interval of 30 s." (2.1 Band 7)

### Imaging

- task: tclean, multi-scale, Briggs weighting  
  > "All imaging was performed with the `tclean` function with a multi-scale approach and Briggs weighting." (2.2 Imaging)
- deconvolver: _not stated_
- weighting robust: Band 3 robust 0; Band 6 robust -1; Band 7 robust 0.5  
  > "Finally, a robust value of 0.5 was chosen for Band 7" (2.2 Imaging)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Keplerian mask (i=6.8 deg, PA=151 deg, M=0.65 Msun, 60.1 pc), convolved with 1" Gaussian; threshold 2x dirty-image RMS  
  > "was set to twice this value" (2.2 Imaging)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Convolved to common 0.6"x0.5" beam at PA 60 deg with CASA imsmooth for excitation analysis  
  > "with a target resolution of $0.6\ensuremath{''} \times 0.5\ensuremath{''}$ at a position angle of $60\ensuremath{^\circ}$" (6.2 Fitting)
- final beam: _not stated_
- final rms: 2.7 (B3), 5.2 (B6), 3.6 (B7) mJy/beam in a line-free channel  
  > "an RMS of $5.2~{\rm mJy~beam^{-1}}$ in a line-free channel" (2.2 Imaging)

### Inherited from earlier work

- Line shifting and stacking technique  
  > "we follow the line shifting and stacking technique described in (cite: Teague_ea_2016) and (cite: Yen_ea_2016)" (2.3 Observational Results) [from Teague_ea_2016; Yen_ea_2016]
- LTE Tex fitting method  
  > "following the method described in (cite: Hily-Blant_ea_2013)" (3.1 Excitation Temperature) [from Hily-Blant_ea_2013]
- Rotation curve inference with Gaussian Process  
  > "for each annulus we follow the method described in (cite: Teague_ea_2018c) to infer the projected rotational velocity" (2.3 Observational Results) [from Teague_ea_2018c]
- Forward modeling of beam broadening for Tkin  
  > "we follow a similar forward modeling approach as used in (cite: Teague_ea_2016)" (6 Measuring the Kinetic Temperature) [from Teague_ea_2016]
- Spectral response convolution (Hanning/boxcar)  
  > "Following (cite: Loomis_ea_2018a) we adopt a Hanning function for the Band 3 data" (6.2 Fitting) [from Loomis_ea_2018a]

### Not stated but needed to reproduce (our reading)

- Band 6 and 7 flux/bandpass/phase calibrators
- CASA and pipeline versions
- Line-free channels and continuum subtraction details
- Cell and image size, multiscale scales
- Spectral averaging details (8 and 16 channels stated only in appendix)
- Inclination 6.8 vs 6.5 deg inconsistency between uses
- Priors on tau0 and Tkin parameters
- Observing configuration details of Band 7 flux calibration

## Analysis recipe

1. **Image cubes**: tclean with Keplerian mask and Briggs weighting, per band  
  > "All imaging was performed with the `tclean` function with a multi-scale approach and Briggs weighting." (2.2 Imaging)
   - software: CASA tclean
   - parameter: robust 0 / -1 / 0.5 for Bands 3/6/7  
  > "a robust value of -1 was adopted" (2.2 Imaging)
   - fitting: _not stated_
   - validation: _not stated_
2. **Stack spectra and measure rotation/stellar mass and fluxes**: Annuli of beam/4 width; Gaussian-process rotation curve; Keplerian fit; shift and stack; integrate over 1.5 km/s window; matched filter check  
  > "To verify the detection of weak components with the image stacking, we used a matched-filter approach implemented in `VISIBLE`" (2.3 Observational Results)
   - software: GoFish, VISIBLE
   - parameter: inclination 6.5 deg, PA 151 deg; 1.5 km/s window; 40 m/s binning  
  > "assuming an inclination of $6.5\ensuremath{^\circ}$ and a position angle of $151\ensuremath{^\circ}$" (2.3 Observational Results)
   - fitting: Keplerian profile fit to rotation curves  
  > "We obtain a projected rotation curve for each fine-structure group, which are then fit with a Keplerian rotation profile." (2.3 Observational Results)
   - validation: Consistent with previous sqrt(M)sin i  
  > "This is consistent with previously determined $\sqrt{M_{\rm star}} \sin(i)$ measurements" (2.3 Observational Results)
3. **Fit blended hyperfine components**: Two offset Gaussians with shared width and independent amplitudes  
  > "we fit the profile with two offset Gaussians which sharing the same line width but independent amplitudes" (2.4 Blended Components)
   - assumption: negligible blending between components  
  > "Making the assumption that blending between the components is negligible" (2.4 Blended Components)
   - fitting: _not stated_
   - validation: Compared with higher-resolution data of Hily-Blant+2017  
  > "comparison with higher spectral resolution data published in (cite: Hily-Blant_ea_2017) (their Fig. C.3) confirms the presence of this feature" (2.4 Blended Components)
4. **Infer excitation temperature**: Isothermal slab model with {Tex, dV, tau0} per fine-structure group in 0.1" annuli, full Planck function, convolved with spectral response  
  > "it is possible to model the emergent intensity from an isothermal slab with only $\{T_{\rm ex},\, \Delta V,\, \tau_0\}$" (3.1 Excitation Temperature)
   - software: emcee, scipy.optimize, CASA imsmooth
   - parameter: emcee: walkers = 2x free parameters, 2000 burn-in + 10000 steps; Nelder-Mead start  
  > "Each walker took 2,000 steps to burn in, then an additional 10,000 to sample the posterior distribution." (6.2 Fitting)
   - assumption: shared Tex within group; Gaussian profiles; optical depths summed  
  > "We assume that each fine structure group shares a common excitation temperature" (6.1 Method)
   - fitting: emcee; Gaussian prior on Tex tied to dV with delta=0.23; weak components r_i<0.02 not fit  
  > "where $\delta = 0.23$, equivalent to previous limits on non-thermal broadening" (6.2 Fitting)
   - validation: Fits to integrated and peak fluxes give same results  
  > "We find no difference between these results and the full spectrum fits" (3.1 Excitation Temperature)
5. **Infer kinetic temperature**: Forward model beam-broadened dV profile with broken power-law Tkin(r), compare to observed dV  
  > "the temperature was parameterised as a broken power law profile of the form" (7.1 Method)
   - software: emcee, scipy.optimize.curve_fit
   - parameter: 12 walkers, 2000 burn-in + 2000 steps; fit 0.3"-3.0"; pivot at 1"  
  > "12 walkers were used for each fit" (7.2 Modeling)
   - assumption: purely thermal broadening, mu_CN=26, Mstar=0.65 Msun, i=6.8 deg  
  > "The width was assumed to be entirely thermally broadened" (7.1 Method)
   - fitting: _not stated_
   - validation: Single vs double power law gave comparable results; individual Gaussian fits to check blending  
  > "Both single and double power law profiles of the underlying $T_{\rm kin}$ profile were tested and gave comparable results." (3.2 Kinetic Temperature)
6. **Non-LTE test with RADEX**: Compute Tex scatter within fine-structure groups versus H2 density  
  > "we calculate the excitation temperatures for a range of H$_2$ collider densities assuming a thermal H$_2$ ortho-para distribution" (4.1 Non-LTE Excitation)
   - software: RADEX
   - parameter: Tkin=24 K, N(CN)=1e14 cm^-2, thermalised linewidth  
  > "a CN column density of $N({\rm CN}) = 10^{14}~{\rm cm^{-2}}$" (4.1 Non-LTE Excitation)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : tclean imaging and imsmooth  
  > "This was achieved with the `imsmooth` task in `CASA`" (6.2 Fitting)
- **GoFish** : line shifting, stacking, radial profiles  
  > "implemented in the Python package `GoFish`" (2.3 Observational Results)
- **VISIBLE** : matched filter detection  
  > "a matched-filter approach implemented in `VISIBLE`" (2.3 Observational Results)
- **emcee** : MCMC posteriors  
  > "The Affine-invariant MCMC ensemble sampler `emcee` was used" (3.1 Excitation Temperature)
- **RADEX** : non-LTE excitation  
  > "we use the 0-D non-LTE radiative transfer code `RADEX`" (4.1 Non-LTE Excitation)
- **scipy** : Nelder-Mead and curve_fit optimisation  
  > "the ‘Nelder-Mead’ algorithm in `scipy.optimize.minimize`" (6.2 Fitting)
- **GILDAS/CLASS** : comparison fitting method with Rayleigh-Jeans approximation  
  > "slightly difference from the one in the `GILDAS/CLASS` software" (6.1 Method)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Stellar mass from rotation | 0.66 | 0.02 | Msun | 2 | $M_{\rm star} = 0.66 \pm 0.02~M_{\rm sun}$ |
| Average Tex (0.5"-3") | 27 | 7 | K | 4 | $\langle T_{\rm ex} \rangle = 27 \pm 7$ K |
| Average Tkin (0.5"-3") | 24 | 5 | K | 5 | $\langle T_{\rm kin} \rangle = 24 \pm 5$ K |
| Tkin,0 N=1-0 J=3/2-1/2 | 28 | 3 | K | 5 | $28 \pm 3$ K |
| Detected hyperfine transitions | 24 of 30 | not stated | dimensionless | 2 | 24 hyperfine transitions are detected out of the 30 |
| Splitting of 340.247770 GHz blend | 334 | not stated | kHz | 3 | 334 kHz for the 340.247770 GHz components and 295 kHz for the 340.035408 GHz components |
| Splitting of 340.035408 GHz blend | 295 | not stated | kHz | 3 | 334 kHz for the 340.247770 GHz components and 295 kHz for the 340.035408 GHz components |

## Qualitative findings

- CN emission shows a ring peaking near 0.7" (42 au) with an outer tail to ~180-200 au in all transitions  
  > "a broad ring peaking at 0.7$''$ (42 au), with a broader excess out to $\approx 3\ensuremath{''}$ (180 au)" (2.3 Observational Results)

## Claim tuples

- H: Is CN in TW Hya in LTE? | E: LTE slab fits to Tex and forward-modelled Tkin for four fine-structure groups | R: Tex exceeds Tkin over large radial ranges, most for N=3-2 | F: LTE assumptions are invalid; non-LTE effects are present | **supported**
- H: At what density does non-LTE appear? | E: RADEX Tex scatter versus n(H2) | R: deviations for n_H2 <~ 1e7 cm^-3 | F: CN arises where z/r >~ 0.2, consistent with UV-driven formation | **partially**
- H: Can stacking resolve blended hyperfine lines? | E: Two-Gaussian fits to stacked spectra | R: splittings of ~295 and 334 kHz | F: Splittings larger than laboratory uncertainties | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Hyperfine multiplets within one tuning avoid multi-band flux calibration uncertainty  
  > "This can be circumvented by using molecules with (hyper-)fine structure lines" (Introduction)
- Alternative: Single power law Tkin profile found too inflexible  
  > "A single power law profile was initially adopted but was found to be too inflexible to to match the data." (7.1 Method)
- How they decided it was enough: _not stated_
- Limitation (authors): Tex modelling assumes independent optical depths and no treatment of blends, problematic when tau >~ 1  
  > "In this regime such blended components may causes issues" (4.1 Non-LTE Excitation)
- Caveat (inferred, ours): Tex>Tkin could result from model assumptions rather than non-LTE
- Caveat (inferred, ours): Density constraint depends on a single RADEX setup and external disk model
- Caveat (inferred, ours): Missing short spacings in Band 7 cause negative flux
- Caveat (inferred, ours): Low spectral resolution in Band 7 limits blend fits

## Reproducibility

- Data public (paper): ALMA project codes given; products from archive implied  
  > "This paper makes use of the following ALMA data: 2013.1.00387.S, 2016.1.00440.S and 2017.1.01199.S." (Acknowledgments)
- Products in archive: _not stated_
- Code: Keplerian mask code at github.com/richteague/keplerian_mask; GoFish and VISIBLE public  
  > "The code to make Keplerian masks is available from <https://github.com/richteague/keplerian_mask>" (footnote 1)
- Missing: Calibrators for Bands 6 and 7
- Missing: CASA version
- Missing: Line-free channels and cleaning parameters
- Data volume (inferred): ~100-300 GB raw across three projects
- Score (inferred): 6/5, Data are public and the method is well described with MCMC settings, but imaging and calibration details are missing.
- Rediscovery candidate: yes, Public data, numeric Tex/Tkin results, and a mostly complete recipe.

## Links

- Method: Hily-Blant et al. 2013 (LTE Tex fitting method)
- Method: Teague et al. 2018 (Teague_ea_2018c) (rotation curve inference)
- Method: Teague 2019 (GoFish) (stacking code)
- Companion: Teague et al. 2016 (previous CN N=2-1 analysis of the same Band 6 data)
- Companion: Hily-Blant et al. 2017 (CN N=3-2 analysis)

## Checks

```json
{
 "quotes": 86,
 "quotes_ok": 86,
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
  "facts": 88,
  "stated": 60,
  "rate": 0.682
 },
 "evidence_ok": true
}
```
