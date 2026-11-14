# Detection of Infall in the Protostar B335 with ALMA

`2015ApJ...814...22E` | The Astrophysical Journal 2015 | first author: Evans, Neal J., II | arXiv: 1510.03476 | DOI: 10.1088/0004-637X/814/1/22

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: Is there unambiguous infall toward the Class 0 protostar B335, seen as redshifted absorption against the continuum, and can an inside-out collapse model reproduce the HCN and HCO+ profiles?  
  > "Our goal is to see if a previously developed physical model can account approximately for the observed line profiles." (Models)
- Target **B335**: coordinates 19:37:00.894, +07:34:09.59 (J2000)  
  > "A two-dimensional Gaussian fit yields a source centered at 19:37:00.894, $+$07:34:09.59 (J2000)" (Results); "The recently revised distance to B335 of $105 \pm 15$ pc (cite: 2009A&A...498..455O)" (Introduction); z/distance 100 pc adopted (105 ± 15 pc)  
  > "A two-dimensional Gaussian fit yields a source centered at 19:37:00.894, $+$07:34:09.59 (J2000)" (Results); "The recently revised distance to B335 of $105 \pm 15$ pc (cite: 2009A&A...498..455O)" (Introduction); distance from Olofsson & Olofsson 2009  
  > "A two-dimensional Gaussian fit yields a source centered at 19:37:00.894, $+$07:34:09.59 (J2000)" (Results); "The recently revised distance to B335 of $105 \pm 15$ pc (cite: 2009A&A...498..455O)" (Introduction)

## Data provenance

- ALMA projects: 2012.1.00346.S
- bands: Band 7  
  > "The observations used 35 12-m antennas and the Band 7 receivers." (Observations)
- frequencies and spectral setup: 4 spws, 3840 channels of 61.035 kHz (~0.05 km/s), 234.375 MHz usable bandwidth each; HCN 4-3, HCO+ 4-3, CS 7-6, H13CN 4-3 in spws 0-3  
  > "The ALMA Correlator was configured to have four spectral windows (spws), each with 3840 channels 61.035 kHz ($\sim 0.05$ km s$^{-1}$) wide" (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C32-3, ALMA Early Science  
  > "in the C32-3 configuration of ALMA Early Science" (Observations)
- baselines: 18.69 m to 527.57 m  
  > "Data of B335 were obtained over a baseline range of 18.69 m to 527.57 m." (Observations)
- angular resolution: 0.486" x 0.439", PA -76.9 deg (continuum)  
  > "The resolution of the CLEAN continuum image was $0.486\ensuremath{''} \times 0.439\ensuremath{''}$, P.A. = $-76.9^{\circ}$." (Observations)
- max recoverable scale: Half the flux of a Gaussian with FWHM 4.1" recovered  
  > "Half the flux of a Gaussian with FWHM size of 4.1$''$ would be recovered with this minimum baseline" (Observations)
- sensitivity: _not stated_
- time on source: 48.35 min on B335 (97 min execution block)  
  > "B335 was observed for a total of 48.35 minutes." (Observations)
- observing dates: 27 April 2014 (UT)  
  > "on 27 April 2014 (UT)" (Observations)
- pi or archival as stated: PI N. Evans project  
  > "project 2012.1.00346.S (PI. N. Evans)" (Observations)
- Line: HCN J=4-3 (354.505470 GHz)
- Line: HCO+ J=4-3 (356.734240 GHz)
- Line: CS J=7-6 (342.882860 GHz)
- Line: H13CN J=4-3 (345.339760 GHz)
- External data: 0.8 mm continuum 350 mJy over 1.6" at 19:37:00.91, +07:34:09.6  
  > "found a continuum source at 0.8 mm at 19:37:00.91, $+$07:34:09.6 (J2000), with a size of $1.6\ensuremath{''}$, and a total flux density of 350 mJy." (Results) [from Jørgensen et al. 2007 (cite: 2007ApJ...659..479J)]
- External data: Average 850 um dust opacity for B335 of 1.48e-2 cm2 per gram of gas (gas-to-dust 100)  
  > "1.48${} \times 10^{-2}$ cm$^2$ per gram of gas for a gas to dust ratio of 100" (4.3 Updated Model and Uncertainties) [from Shirley et al. 2011 (cite: 2011ApJ...728..143S)]
- External data: Systemic velocity 8.30 ± 0.05 km/s  
  > "systemic velocity of $8.30\pm 0.05$ km s$^{-1}$ (cite: 2005ApJ...626..919E)" (Results) [from Evans et al. 2005 (cite: 2005ApJ...626..919E)]
- External data: Outflow force scaled to 100 pc: 1.4e-5 Msun/yr km/s  
  > "yields a value of 1.4${} \times 10^{-5}$ M$_\odot$ yr$^{-1}$ km s$^{-1}$" (4.3 Updated Model and Uncertainties) [from Cabrit & Bertout 1992 (cite: 1992A&A...261..274C)]

## Processing

### Calibration

- pipeline or manual: NAASC calibration with standard CASA procedures, then further calibration by project team in CASA  
  > "The data were initially calibrated and imaged by staff at the North American ALMA Science Center (NAASC), using standard procedures in the Common Astronomy Software Applications (CASA) package." (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1751+096 (amplitude); J1924-2914 bandpass; J1955+1358 phase  
  > "then a $\sim$2.5 minute integration on J1751+096 to calibrate amplitudes." (Observations)
- flux scale uncertainty: _not stated_
- self calibration: Phase at 600 s, phase at 60 s, then amplitude at 3600 s, on smoothed line-free channels; applied to unsmoothed data  
  > "The data were self-calibrated in phase first at 600 sec intervals followed by another self-calibration in phase at 60 sec intervals." (Observations); "The data were then self-calibrated in amplitude over 3600 sec intervals." (Observations)

### Imaging

- task: _not stated_
- deconvolver: Clark CLEAN; continuum threshold 0.5 mJy (~2 sigma); line 60 mJy per channel  
  > "The dirty image was CLEANed using the basic Clark algorithm down to a threshold of 0.5 mJy, roughly 2 $\sigma$." (Observations)
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: 0.1" x 0.1"  
  > "a field with 512 $\times$ 512 cells of $0.1\ensuremath{''} \times 0.1\ensuremath{''}$ size each" (Observations)
- image size: 512 x 512 cells  
  > "a field with 512 $\times$ 512 cells" (Observations)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Image plane, MIRIAD; polynomial fit to line-free channels, first-order for HCO+, HCN, CS and zeroth-order for H13CN  
  > "The polynomials were first-order for the HCO$^{+}$, HCN, and CS cubes, but zeroth-order for the H$^{13}$CN cube due to an abundance of lines in that spectrum." (Observations)
- line free channels: _not stated_
- primary beam correction: Applied to continuum and line data  
  > "The continuum and line data were corrected for primary beam attenuation." (Observations)
- array combination: _not stated_
- smoothing: Hanning smoothing to 0.2 km/s for channel maps  
  > "Channel maps were created after an additional Hanning smoothing to an effective resolution of 0.2 km s$^{-1}$." (Results)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Modeling apparatus (inside-out collapse, dust and gas thermal codes, Monte Carlo line transfer) and best-fit infall radius  
  > "We use the same modeling apparatus as we used in" (4.2 Simple Models of Line Emission: Pure Infall) [from Evans et al. 2005 (cite: 2005ApJ...626..919E)]
- Drop abundance profile form  
  > "For the HCN line, a drop function" (4.2 Simple Models of Line Emission: Pure Infall) [from Jørgensen et al. 2004 (cite: 2004A&A...416..603J)]
- Mass from continuum using eq. A.31 and mass-weighted dust temperature eq. 8  
  > "using equation A.31 of" (4.3 Updated Model and Uncertainties) [from Kauffmann et al. 2008 (cite: 2008A&A...487..993K)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges for continuum and baseline
- CASA version
- Whether tclean or clean was used and whether clean masks were applied
- uv weighting/robust
- Model velocity field and shell structure details are only in Evans 2005
- Mass-weighted dust temperature model details
- Model beam/spectral convolution details
- Exact fit procedure for abundances (done by eye?)

## Analysis recipe

1. **Self-calibrate and image continuum and line cubes**: Self-calibration on smoothed line-free data, MFS continuum imaging, Clark CLEAN of continuum and each channel  
  > "A smoothed version of the data was self-calibrated using line-free channels to create a continuum dataset." (Observations)
   - software: CASA
   - parameter: Cell 0.1", 512x512, thresholds 0.5 mJy (continuum) and 60 mJy per channel  
  > "down to a threshold of 60 mJy per channel, again $\sim$2 $\sigma$." (Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Subtract continuum in image plane**: Polynomial fit to line-free channels, subtracted in image plane to avoid artifacts with absorption  
  > "Continuum subtraction in the uv plane can cause artifacts in the presence of absorption features, so we removed the continuum in the image plane." (Observations)
   - software: MIRIAD
   - fitting: _not stated_
   - validation: _not stated_
3. **Measure continuum and extract spectra**: 2D Gaussian fit to continuum; spectra from 0.5"x0.5" box on source and 0.5" circles north/south as off-source check; converted to TR  
  > "The spectra for all four lines, extracted from a 0.5$''$ by 0.5$''$ box centered on the continuum source, are shown in Figure [4](#almatr)." (Results)
   - fitting: 2D Gaussian  
  > "A two-dimensional Gaussian fit yields a source centered at 19:37:00.894" (Results)
   - validation: Off-source spectra show no absorption below the continuum, confirming absorption confined to the continuum source  
  > "While red-shifted **self**-absorption can be seen, the lines no longer show significant absorption below the continuum." (4.1 General Considerations)
4. **Model line profiles with inside-out collapse**: Shu inside-out collapse with dust and gas thermal codes, Monte Carlo radiative transfer, beam 0.57", 80 shells with inner radius 6 AU, central continuum source, baseline removal; abundance profiles (step for HCO+, drop for HCN) tuned  
  > "we have doubled the number of shells (to 80) in the radiative transport code, extending the inner radius of the model to 6 AU." (4.2 Simple Models of Line Emission: Pure Infall)
   - parameter: r_inf = 0.012 pc; initial T_K = 13 K; c_s,eff = 0.233 km/s  
  > "an effective sound speed (combining thermal and turbulent contributions) of $\mbox{$c_{{\rm s,eff}}$}=  0.233$ km s$^{-1}$" (4.3 Updated Model and Uncertainties)
   - assumption: Distance 100 pc; luminosity 0.72 Lsun  
  > "We take a distance of 100 pc, 0.25 times the distance assumed in the past, for convenience." (Introduction)
   - fitting: Single free parameter r_inf; abundances tuned by hand  
  > "The abundances of the molecules needed tuning on small scales to match the data." (4.2 Simple Models of Line Emission: Pure Infall)
   - validation: Other r_inf tested: smaller fail to match absorption width and wings, larger too wide  
  > "Smaller infall radii fail to predict the width of the red-shifted absorption and the wings of the lines." (4.2 Simple Models of Line Emission: Pure Infall)
5. **Derive infall age, rates, central mass and optically thin mass**: Age = r_inf/c_s; Mdot_inf = 0.975 cs^3/G; mass from 91 mJy continuum within 25 AU via Kauffmann et al. 2008  
  > "The mass infall rate would be $\mbox{$\dot M_{\rm inf}$}= 0.975 c_{\rm s}^3/G = 2.94\mbox{${} \times 10^{-6}$}$ M$_\odot$ yr$^{-1}$" (4.3 Updated Model and Uncertainties)
   - parameter: T_dust mass-weighted 111 K; opacity 1.48e-2 cm2/g; gas-to-dust 100  
  > "We use the mass-weighted dust temperature (equation 8) of (cite: 2008A&A...487..993K) of 111 K" (4.3 Updated Model and Uncertainties)
   - assumption: Constant infall rate, wind mass loss neglected  
  > "if the infall rate has been constant and mass loss in the wind is neglected" (4.3 Updated Model and Uncertainties)
   - fitting: _not stated_
   - validation: Tested initial T_K of 8 K (age 6.1e4 yr)  
  > "Assuming a constant $T_K$ of 8 K, rather than 13 K, would make the age 6.1${} \times 10^{4}$ yr, about 20% larger." (4.3 Updated Model and Uncertainties)

## Software

- **CASA** : Calibration, self-calibration and imaging  
  > "The data were delivered to the project team for further calibration and imaging, again using CASA." (Observations)
- **MIRIAD** : Image-plane continuum subtraction  
  > "Using MIRIAD" (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum flux density at 350 GHz | 91 | 6 | mJy | 3 | The total flux density is $91\pm6$ mJy. |
| Deconvolved continuum size | 0.45" x 0.25" at PA 10 deg | not stated | arcsec | 3 | with a deconvolved size (FWHM) of $0.45\ensuremath{''}$ by $0.25\ensuremath{''}$ at position angle of $10\mbox{$^{\circ}$}$ |
| Infall radius | 0.012 | not stated | pc | 4 | The infall radius of 0.012 pc |
| Age since collapse began | 5.0e4 | not stated | yr | 5 | implies an age of 5.0${} \times 10^{4}$ years |
| Mass infall rate | 2.94e-6 | not stated | Msun/yr | 5 | = 2.94\mbox{${} \times 10^{-6}$}$ M$_\odot$ yr$^{-1}$ |
| Accumulated central mass | 0.15 | not stated | Msun | 5 | allowing a central mass (star and disk) of 0.15 M$_\odot$ to accumulate |
| Optically thin gas+dust mass within 25 AU | 7.5e-4 | not stated | Msun | 5 | The resulting mass is 7.5${} \times 10^{-4}$ M$_\odot$ |
| Accretion rate onto star | 9.6e-7 | not stated | Msun/yr | 5 | we get $\mbox{$\dot M_{\rm acc}$}= 9.6\mbox{${} \times 10^{-7}$}$ M$_\odot$ yr$^{-1}$ |

## Qualitative findings

- HCN and HCO+ show redshifted absorption against the continuum; CS shows red self-absorption but no absorption below the continuum; H13CN shows none  
  > "The H$^{13}$CN spectrum shows no absorption feature." (Results)

## Claim tuples

- H: Does B335 show unambiguous infall? | E: Spectra of four lines extracted toward the continuum peak and off-source | R: Redshifted absorption below the continuum in HCN and HCO+ on source only | F: Infall is clearly detected via the inverse P-Cygni signature | **supported**
- H: Can the inside-out collapse model match the profiles? | E: Model with r_inf = 0.012 pc compared to ALMA spectra | R: Reasonably good fit of peaks, absorption dip and wings, with tuned abundances | F: Infall radius 0.012 pc, rate 3e-6 Msun/yr, age 5e4 yr | **supported**
- H: Is much mass in an optically thin disk? | E: Mass from 91 mJy continuum | R: 7.5e-4 Msun vs 0.15 Msun infallen | F: Disk mass is very small; most accumulated mass is in the star or opaque regions | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Absorption against continuum gives unambiguous infall evidence; high resolution excludes outflow  
  > "Another advantage of very high spatial resolution is that the outflow region may be excluded" (Introduction)
- Alternative: Unrelated foreground layer as the absorber is rejected given B335's isolation and high lower-state energies  
  > "The simplicity and isolation of the B335 globule (cite: 2007A&A...475..281G) make this explanation highly unlikely" (4.1 General Considerations)
- How they decided it was enough: _not stated_
- Limitation (authors): Simple spherical models do not perfectly match; abundance profiles are ad hoc  
  > "The simple, spherical models do not perfectly match the observations." (4.2 Simple Models of Line Emission: Pure Infall)
- Caveat (inferred, ours): Only one free parameter model with hand-tuned abundances; no formal fit or uncertainties
- Caveat (inferred, ours): Luminosity correction (factor 2) from preliminary models
- Caveat (inferred, ours): Mass depends on assumed temperature and opacity
- Caveat (inferred, ours): Single execution block

## Reproducibility

- Data public (paper): ALMA data acknowledged with ADS/JAO code; archive project  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00346.S." (Summary)
- Products in archive: _not stated_
- Missing: Model codes from Evans 2005 not provided
- Missing: CASA version and masks
- Missing: Line-free channels
- Data volume (inferred): ~20-50 GB raw
- Score (inferred): 3/5, Data public and imaging described, but model codes and several settings are not given; fit is by eye.
- Rediscovery candidate: no, The main result relies on an unreleased modeling pipeline with hand-tuned abundances, though the continuum flux and spectra could be redone.

## Links

- Method: Evans et al. 2005 (cite: 2005ApJ...626..919E) (Model apparatus and infall radius)
- Method: Kauffmann et al. 2008 (cite: 2008A&A...487..993K) (Continuum mass estimate)
- Companion: Yen et al. 2015b (cite: 2015arXiv150904675Y) (ALMA C18O and SO study of B335)

## Checks

```json
{
 "quotes": 72,
 "quotes_ok": 72,
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
  "facts": 75,
  "stated": 51,
  "rate": 0.68
 },
 "evidence_ok": true
}
```
