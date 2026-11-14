# ALMA data suggest the presence of spiral structure in the inner wind of CW Leonis

`2015A&A...574A...5D` | Astronomy and Astrophysics 2015 | first author: Decin, L. | arXiv: 1410.2060 | DOI: 10.1051/0004-6361/201424593

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars
- Question: What is the morpho-kinematical structure of the inner wind of the carbon star CW Leo, and does it show a binary-induced spiral?  
  > "We aim to study the inner wind structure of the closest well-known AGB star CW Leo." (abstract)
- Target **CW Leo (IRC +10216)**: coordinates 09:47:57.4553 +13:16:43.749 (J2000), continuum peak  
  > "The position of the 650 GHz continuum peak is 09:47:57.4553 +13:16:43.749 (J2000), epoch 2012.92." (3.1 Astrometry); "CW Leo (a.k.a. IRC +10216) is the nearest carbon-rich Asymptotic Giant Branch (AGB) star at a distance around 120 to 150 pc" (1 Introduction); z/distance 120-150 pc; 150 pc adopted for models  
  > "The position of the 650 GHz continuum peak is 09:47:57.4553 +13:16:43.749 (J2000), epoch 2012.92." (3.1 Astrometry); "CW Leo (a.k.a. IRC +10216) is the nearest carbon-rich Asymptotic Giant Branch (AGB) star at a distance around 120 to 150 pc" (1 Introduction); distance from Menshchikov2001; Groenewegen2012; Decin2010/De Beck2012 for models  
  > "The position of the 650 GHz continuum peak is 09:47:57.4553 +13:16:43.749 (J2000), epoch 2012.92." (3.1 Astrometry); "CW Leo (a.k.a. IRC +10216) is the nearest carbon-rich Asymptotic Giant Branch (AGB) star at a distance around 120 to 150 pc" (1 Introduction)

## Data provenance

- ALMA projects: 2011.0.00277.S
- bands: Band 9, ~650 GHz  
  > "centred at 643.6645, 646.4827, 658.0587 and 661.1205 GHz (ALMA Band 9)." (2.1 ALMA observations)
- frequencies and spectral setup: Four 1.875-GHz spws, 3840 channels of 488 kHz; 0.455 km/s after Hanning  
  > "Each spectral window was divided into 3840 channels of 488 kHz. After Hanning smoothing, the effective velocity resolution is 0.455 km s$^{-1}$." (2.1 ALMA observations)
- continuum bandwidth: _not stated_
- arrays: 18 antennas  
  > "The 18 antennas provided good data, with minimum and maximum baselines of 25 – 340 m." (2.1 ALMA observations)
- configurations: _not stated_
- baselines: 25-340 m  
  > "The 18 antennas provided good data, with minimum and maximum baselines of 25 – 340 m." (2.1 ALMA observations)
- angular resolution: 0.42" x 0.24", PA 117 deg  
  > "The full-resolution images were made with partial uniform weighting to give a synthesized beam 0.42$''$$\times$0.24$''$ for a position angle of 117$^\circ$" (2.2 Data reduction)
- max recoverable scale: ~3" accurate; >6" undetectable  
  > "The shortest baselines in our observations impose a limit of $\sim3$$^{\prime\prime}$ on the size of any structure which can be imaged accurately." (2.2 Data reduction)
- sensitivity: 0.2-0.3 Jy/beam per 488 kHz channel  
  > "The noise in the image cubes is 0.2 – 0.3 Jy beam$^{-1}$ per 488 kHz channel" (2.2 Data reduction)
- time on source: 17.5 min  
  > "The total time on IRC +10216 was 17.5 min spread over 35 min." (2.1 ALMA observations)
- observing dates: 1 December 2012  
  > "IRC +10216 was observed by ALMA on 1 December 2012" (2.1 ALMA observations)
- pi or archival as stated: _not stated_
- Line: 13CO J=6-5 (661.0673 GHz)
- Line: SiS v=2 J=36-35 (646.1000 GHz)
- Line: SiC2 26(4,22)-25(4,21) (645.7526 GHz)
- Other facility **Herschel/HIFI**: Spectral survey for line flux comparison  
  > "The frequency range observed with ALMA was also observed by the Herschel/HIFI instrument" (4.2 Comparison between ALMA and Herschel)
- External data: Stellar luminosity ~15600 Lsun and Teff 2330 K  
  > "which would imply a stellar luminosity of $\sim$15 600 L$_{\odot}$ according to (cite: DeBeck2012A&A...539A.108D)" (3.2 Stellar and dust properties) [from (cite: DeBeck2012A&A...539A.108D)]
- External data: Dust opacity 90 cm2/g at 650 GHz  
  > "for an opacity $\kappa_\lambda$ at 650 GHz of 90 cm$^2$/g (cite: Mennella1998ApJ...496.1058M)" (3.2 Stellar and dust properties) [from (cite: Mennella1998ApJ...496.1058M)]
- External data: PdBI point-source fluxes 65 mJy at 89 GHz and 487 mJy at 242 GHz  
  > "found a ‘point source’ at 89 GHz (3.5 mm) and 242 GHz (1.3 mm) with flux densities of $65\pm7$ mJy and $487\pm70$ mJy, respectively." (3.2 Stellar and dust properties) [from (cite: Lucas1999IAUS..191..305L)]
- External data: Herschel/HIFI survey data  
  > "The data reduction and first results are described in (cite: Cernicharo2010A&A...521L...8C)." (4.2 Comparison between ALMA and Herschel) [from (cite: Cernicharo2010A&A...521L...8C)]
- Simulation/model as data: Shape morpho-kinematical models of Archimedean spiral and shells, run through simobserve to mimic ALMA sampling  
  > "We simulated the effect of the ALMA setup using the CASA task simobserve, with antenna positions and atmospheric conditions matching those used for our observations." (7.2 Morpho-kinematical simulations)

## Processing

### Calibration

- pipeline or manual: Manual CASA reduction with phase-reference solutions and self-calibration  
  > "Normal data reduction procedures were performed in CASA" (2.2 Data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan  
  > "The Cycle 0 flux scale was derived with respect to Titan." (2.1 ALMA observations)
- flux scale uncertainty: 20% in Band 9  
  > "The flux density scale is formally accurate to 20% in Band 9" (2.1 ALMA observations)
- self calibration: Self-cal on continuum model; residual scatter ~5 deg phase, 10% amplitude  
  > "The residual scatter in the final self-calibration solutions was about 5$^\circ$ in phase and 10% in amplitude." (2.2 Data reduction)

### Imaging

- task: CASA clean per channel  
  > "We used CASA to Fourier transform and clean each channel to produce image cubes for all spectral windows." (2.2 Data reduction)
- deconvolver: _not stated_
- weighting robust: partial uniform weighting (intermediate; no robust value given)  
  > "The full-resolution images were made with partial uniform weighting" (2.2 Data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Line-free channels used for continuum, refined with preliminary cube, then subtracted  
  > "Finally, we made a preliminary cube to refine the selection of continuum channels, subtracted these and made the final line and continuum images." (2.2 Data reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: 3-channel averaged images with 0.4"x0.4" beam, ~0.7 km/s  
  > "A beam of 0.4$''$$\times$0.4$''$ was used for the 3-channel averaged images which have a resolution of $\sim$0.7 km/s" (2.2 Data reduction)
- final beam: 0.42"x0.24" PA 117 deg  
  > "synthesized beam 0.42$''$$\times$0.24$''$ for a position angle of 117$^\circ$" (2.2 Data reduction)
- final rms: 0.13-0.18 Jy/beam for 3-channel averaged images  
  > "a noise value of 0.13–0.18 Jy beam$^{-1}$" (2.2 Data reduction)

### Inherited from earlier work

- Phase of observations (0.98 ALMA, 0.46 Herschel) from pulsation ephemeris  
  > "Following (cite: Jenness2002MNRAS.336...14J), the Herschel and ALMA data were taken at phase 0.46 and 0.98, respectively." (4.2 Comparison between ALMA and Herschel) [from (cite: Jenness2002MNRAS.336...14J)]
- Spiral pattern prescription and arm spacing/period relation  
  > "which following (cite: Kim2012ApJ...759L..22K) is given by" (8.2 Orbital period and binary separation) [from (cite: Kim2012ApJ...759L..22K)]
- Detailed hydrodynamical/radiative transfer modeling deferred  
  > "but will be presented in a forthcoming paper (Homan et al., in prep.)." (7 Modeling a binary-induced spiral structure) [from Homan et al., in prep.]

### Not stated but needed to reproduce (our reading)

- CASA version
- clean threshold, niter, mask, and robust/uniform weighting parameter
- line-free channel ranges for continuum
- self-calibration solution intervals
- Shape model files and full parameter set (orientation angles, PA)
- Exact simobserve settings
- How the best-fit spiral was judged (visual comparison, no statistic)

## Analysis recipe

1. **Calibrate, self-calibrate and image**: CASA reduction, continuum self-cal, continuum subtraction, per-channel clean cubes  
  > "We used these to make a continuum image, which provided a model for self-calibration of all the target continuum data." (2.2 Data reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: Checked sidelobe and cereal-bowl artifacts  
  > "We took care to check that any apparently symmetric structures were not in fact co-incident with sidelobes." (2.2 Data reduction)
2. **Measure continuum and positions**: 2D Gaussian fits to continuum peak and line zeroth moments; subtract 2.3 Jy point source for dust  
  > "We measured the positions and extents of emission by fitting 2D Gaussian components to the continuum peak and to the zeroth moment of each line" (2.3 Position measurements)
   - software: CASA
   - assumption: Stellar flux 2.3 Jy at 650 GHz; dust optically thin; kappa=90 cm2/g  
  > "We estimated the 650 GHz emission from dust by subtracting a 2.3 Jy point source, convolved with the natural synthesised beam, from the continuum image" (3.2 Stellar and dust properties)
   - fitting: _not stated_
   - validation: Compared to VLA astrometry and SMA flux  
  > "used the VLA in 2006.16 to measure the position and proper motion of IRC +10216 which would give 09:47:57.4417 +13:16:43.896 in 2012.92 (uncertainty $0.012\ensuremath{''}$)." (3.1 Astrometry)
3. **Line widths and sizes**: Soft-parabola fit to spectra from 1.2" aperture; 2D Gaussian FWHM on first moment of inner 10 km/s  
  > "each line has been fitted using the soft-parabola line profile (cite: Olofsson1993ApJS...87..267O)" (4.1 ALMA spectra of CW Leo in band 9)
   - software: CASA
   - fitting: soft-parabola profile  
  > "each line has been fitted using the soft-parabola line profile" (4.1 ALMA spectra of CW Leo in band 9)
   - validation: Compared with Herschel/HIFI line widths and fluxes  
  > "The half line width at continuum level, $v_{\rm{line}}$, of all common unblended lines is in agreement for both instrument." (4.2 Comparison between ALMA and Herschel)
4. **PV diagrams**: impv with 201 slits, 1 pixel wide, 101 pixels long, at various PA  
  > "In the standard set-up, 201 slits with a width of 1 pixel ( = 0.060$^{\prime\prime}$) and a length of 101 pixels ( = 6.06$^{\prime\prime}$) were taken." (5.2 Position-velocity diagrams and morphology)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
5. **Model spiral in 13CO PV**: Shape/Shapemol Archimedean spiral models passed through simobserve and compared with observed PV  
  > "As setup for our basic spiral model, we chose as free parameters $i=80$$^\circ$ (cite: Jeffers2014), $a=1.45$$^{\prime\prime}$, $p=2$, $b=0$" (7.2.2 PV-diagram for binary-induced spiral wind structure)
   - software: Shape, Shapemol, CASA simobserve
   - parameter: best fit a=1.12", p=2, b=0, c=3e12 cm, w=30 deg, i=60-80 deg  
  > "A good fit to correlated structures in the ALMA PV data is obtained for the spiral parameters $a=1.12\hbox{$^{\prime\prime}$}$, $p=2$, $b=0$, $c=3\times 10^{12}$ cm, and $w=30\hbox{$^\circ$}$, and $i=60-80$$^\circ$" (8.1)
   - assumption: Distance 150 pc, Mdot 1.5e-5 Msun/yr, CO/H2 6e-4, 12CO/13CO 30, v=14.5 km/s, density divided by 100  
  > "a distance of 150 pc, a constant gas mass-loss rate of 1.5$\times$10$^{-5}$ M$_{\odot}$/yr, a fractional abundance \[CO/H$_2$\] of 6$\times$10$^{-4}$" (7.2)
   - fitting: Manual parameter exploration; no statistical fit  
  > "Each of the parameters is then changed one after the other to demonstrate its effect" (7.2.2 PV-diagram for binary-induced spiral wind structure)
   - validation: _not stated_
6. **Orbital period, separation, companion mass**: Arm spacing to period via Kim & Taam relation; Kepler's third law; Huggins et al. relation for mass  
  > "The derived arm spacing hence results in an orbital period of $\sim$55 yr." (8.2)
   - assumption: Primary mass 4 Msun, companion less massive  
  > "assuming a primary initial mass of 4 M$_{\odot}$ for CW Leo" (8.2)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Reduction, imaging, impv, simobserve  
  > "Normal data reduction procedures were performed in CASA" (2.2 Data reduction)
- **Shape** : Morpho-kinematical modelling  
  > "The simulations are obtained using the Shape software" (7 Modeling)
- **Shapemol** : LVG non-LTE radiative transfer  
  > "a non-LTE (non local-thermodynamic equilibrium) radiative transfer solver (Shapemol) has been added" (7.2)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total continuum flux density within 3 sigma | 5.66 | 20% flux scale | Jy | 2 | The total flux density within the $3\sigma$ contour is 5.66 Jy |
| Continuum peak | 4.362 | 0.023 noise | Jy/beam | 2 | The continuum peak is 4.362 Jy beam$^{-1}$ with a noise uncertainty of 0.023 Jy beam$^{-1}$ |
| Dust mass within 0.8" | 3-6e-7 | not stated | Msun | 2 | we obtain a dust mass within 0.8$^{\prime\prime}$ of 3–6$\times$10$^{-7}$ M$_{\odot}$ |
| Spiral arm spacing a | 1.12 | ~10% | arcsec | 5 | The best constrained parameter is the spiral arm distance $a$, with an uncertainty of only $\sim$10%. |
| Orbital period | 55 | not stated | yr | 6 | The derived arm spacing hence results in an orbital period of $\sim$55 yr. |
| Binary separation | 25 | 2 | au | 6 | the mean binary separation, $d$, for CW Leo is $\sim$25$\pm$2 au |
| Companion mass (Huggins relation) | ~1.1 | significant | Msun | 6 | the derived mass for the secondary, $M_s$, is $\sim$1.1 M$_{\odot}$ |

## Qualitative findings

- Vibrational lines trace the region close to the star and SiO is a parent molecule  
  > "The images prove that vibrational lines are excited close to the stellar surface and that SiO is a parent molecule." (abstract)

## Claim tuples

- H: Does the 13CO PV structure require a binary-induced spiral rather than spherical shells? | E: Compare ALMA PV diagrams at several PA with Shape models of shells and spirals processed through simobserve | R: Spiral at i=60-80 deg reproduces the S-shape and PA asymmetry; shell models do not | F: A binary-induced spiral seen nearly edge-on explains the data | **partially**
- H: How does the wind accelerate in the inner envelope? | E: Line widths vs spatial size of 25 lines | R: Velocity rises from ~5 R* to near terminal at ~11 R* | F: Rapid acceleration within ~11 R* | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Localized radial ejections and rotating latitudinal bands need heavy fine-tuning compared with a spiral  
  > "this scenario would need a lot of finetuning to get a model showing almost symmetrical signatures" (8.4 Other scenarios)
- How they decided it was enough: _not stated_
- Limitation (authors): Short observation and sparse uv coverage hamper interpretation  
  > "With an on-source integration time of only 17 minutes, an in-depth understanding of the $^{13}$CO J=6-5 channel maps" (8.1)
- Caveat (inferred, ours): Spiral interpretation rests on visual PV comparison with a simple parametric model, no goodness-of-fit
- Caveat (inferred, ours): Fragmentation partly artifact from uv gaps
- Caveat (inferred, ours): Companion mass poorly constrained
- Caveat (inferred, ours): Stellar flux contribution uncertain

## Reproducibility

- Data public (paper): Project code and ALMA acknowledgement given  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00277.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: CASA version and clean parameters
- Missing: Shape model files
- Missing: Fit procedure for spiral parameters
- Data volume (inferred): ~10-30 GB raw Cycle 0 Band 9 data
- Score (inferred): 4/5, Public Cycle 0 data and described reduction, but cleaning and Shape modelling details are missing and the modelling is qualitative.
- Rediscovery candidate: no, Key results rely on interactive Shape modelling without full recipe.

## Links

- Method: (cite: Steffen2006RMxAA..42...99S) (Shape modelling tool)
- Method: (cite: Kim2012ApJ...759L..22K) (Arm spacing to orbital period relation)
- Companion: Homan et al., in prep. (Detailed hydrodynamical and radiative transfer modelling)
- Companion: (cite: Maercker2012Natur.490..232M) (ALMA spiral in R Scl)
- Related: Herschel/HIFI spectral survey of IRC +10216

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
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 80,
  "stated": 54,
  "rate": 0.675
 },
 "evidence_ok": true
}
```
