# ALMA Compact Array observations of the Fried Egg nebula. Evidence for large-scale asymmetric mass-loss from the yellow hypergiant IRAS 17163-3907

`2017A&A...597A..99W` | Astronomy and Astrophysics 2017 | first author: Wallström, S. H. J. | arXiv: 1612.02510 | DOI: 10.1051/0004-6361/201628416

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars, stellar_physics
- Question: What is the morphology, kinematics and mass-loss of the circumstellar environment of the yellow hypergiant IRAS 17163-3907, as seen in CO 2-1 with the ACA?  
  > "To further constrain the properties of the circumstellar envelope of IRAS 17163, particularly the mass-loss rate and kinematics" (Introduction)
- Target **IRAS 17163-3907 (Fried Egg nebula, Hen 3-1379)**: coordinates mosaic center RA 17:19:49.335, Dec -39:10:37.94 (J2000)  
  > "The mosaic was centered on R.A. 17:19:49.335 and Dec $-$39:10:37.94 (J2000)" (2.1 ALMA Compact Array data); "the distance (4$\pm$0.5 kpc) to this object has been well constrained by the presence of interstellar absorption lines in its optical spectra" (Introduction); z/distance 4±0.5 kpc  
  > "The mosaic was centered on R.A. 17:19:49.335 and Dec $-$39:10:37.94 (J2000)" (2.1 ALMA Compact Array data); "the distance (4$\pm$0.5 kpc) to this object has been well constrained by the presence of interstellar absorption lines in its optical spectra" (Introduction); distance from Lagadec et al. 2011, interstellar absorption lines in optical spectra  
  > "The mosaic was centered on R.A. 17:19:49.335 and Dec $-$39:10:37.94 (J2000)" (2.1 ALMA Compact Array data); "the distance (4$\pm$0.5 kpc) to this object has been well constrained by the presence of interstellar absorption lines in its optical spectra" (Introduction)

## Data provenance

- ALMA projects: 2013.1.00502.S
- bands: _not stated_
- frequencies and spectral setup: two 1.875 GHz windows at 0.977 MHz channels centred 230.481 and 217.047 GHz; two 2 GHz continuum windows at 15.6 MHz centred 215.9 and 231.5 GHz  
  > "Two spectral windows 1.875 GHz wide were set up with 0.977 MHz channel spacing, centered at 230.481 GHz (upper side band, covering the CO 2-1 transition)" (2.1 ALMA Compact Array data); "centered at frequencies of 215.9 and 231.5 GHz" (2.1 ALMA Compact Array data)
- continuum bandwidth: _not stated_
- arrays: ACA  
  > "IRAS 17163 was observed as part of project 2013.1.00502.S with the ALMA Compact Array (ACA)" (2.1 ALMA Compact Array data)
- configurations: _not stated_
- baselines: ~5 to 45 m  
  > "The projected baselines ranged between $\sim$5 and 45 m" (2.1 ALMA Compact Array data)
- angular resolution: 8.4'' x 4.3'' (PA 96.5 deg), natural weighting  
  > "resulted in a synthesized beam of $8.4'' \times 4.3''$ (with a position angle of 96.5$^\circ$) at the frequency of the CO 2-1 line, using natural weighting" (2.1 ALMA Compact Array data)
- max recoverable scale: ~30''  
  > "giving a maximum recoverable scale of $\sim$30$''$" (2.1 ALMA Compact Array data)
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 25-27 July 2014  
  > "between the 25$^\mathrm{th}$ and 27$^\mathrm{th}$ of July 2014" (2.1 ALMA Compact Array data)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (not stated)
- Line: H30alpha recombination line (231.9 GHz)
- Line: SiO 5-4 (not stated)
- Other facility **APEX**: 13CO 2-1 spectrum (APEX-1) and previously published 12CO spectra  
  > "The $^{13}$CO 2-1 transition at 220.4 GHz was observed in a single pointing centered on IRAS 17163" (2.2 APEX data)
- External data: Stellar parameters (distance, effective temperature, luminosity) used in the wind model  
  > "we take the stellar parameters (distance, effective temperature, luminosity) from (cite: Lagadec:2011aa)" (3.3 The stellar wind) [from (cite: Lagadec:2011aa)]
- External data: 12CO 2-1 APEX spectrum for the 12CO/13CO ratio  
  > "compared with the $^{12}$CO spectrum from (cite: Wallstrom:2015aa)" (3.5 The spur) [from (cite: Wallstrom:2015aa)]
- External data: Herschel dust ring (25'' radius) and SED fit  
  > "a cool dust ring seen with *Herschel* (cite: Hutsemekers:2013aa), with a radius of 25$''$" (3 Results) [from (cite: Hutsemekers:2013aa)]
- External data: CO collisional cross-sections  
  > "uses collisional cross-sections from (cite: Yang:2010aa)" (3.3 The stellar wind) [from (cite: Yang:2010aa)]

## Processing

### Calibration

- pipeline or manual: standard calibration in CASA, no details  
  > "Data were calibrated and imaged in a standard way using CASA" (2.1 ALMA Compact Array data)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "at the frequency of the CO 2-1 line, using natural weighting" (2.1 ALMA Compact Array data)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub, first order polynomial fit to line-free channels  
  > "Continuum was subtracted from the line emission data by using the CASA task *uvcontsub* and fitting a first order polynomial to line-free channels." (2.1 ALMA Compact Array data)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Hanning smoothing, 1.7 km/s velocity resolution  
  > "The velocity resolution for these windows is 1.7 $\mathrm{km\,s^{-1}}$ after Hanning smoothing." (2.1 ALMA Compact Array data)
- final beam: 8.4'' x 4.3'', PA 96.5 deg  
  > "synthesized beam of $8.4'' \times 4.3''$ (with a position angle of 96.5$^\circ$)" (2.1 ALMA Compact Array data)
- final rms: _not stated_

### Inherited from earlier work

- Same APEX off-position as earlier APEX observations  
  > "with the same fixed off-position used by (cite: Wallstrom:2015aa)" (2.2 APEX data) [from (cite: Wallstrom:2015aa)]
- Wind radiative transfer: Monte Carlo CSE model  
  > "radiative transfer is solved using a Monte Carlo method (cite: Bernes:1979aa; Schoier:2001ab)" (3.3 The stellar wind) [from (cite: Bernes:1979aa; Schoier:2001ab)]

### Not stated but needed to reproduce (our reading)

- CASA version and pipeline details
- Calibrators and flux scale
- Image size, cell size, deconvolver, masking, clean threshold
- Line-free channels used for uvcontsub
- Mosaic imaging details and primary beam correction
- Final rms noise
- Model grid ranges and step sizes for mass-loss rate and expansion velocity
- Spectral window used for the H30alpha Gaussian fit and baseline treatment
- Which channels were excluded as ISM/spur in the chi2 fit
- Details of the RADEX grid ranges

## Analysis recipe

1. **image CO 2-1, continuum and H30alpha**: Standard CASA calibration and imaging; continuum from line-free channels of coarse windows; uvcontsub on line data  
  > "Data were calibrated and imaged in a standard way using CASA" (2.1 ALMA Compact Array data); "obtained by aggregating all line-free channels in the coarse spectral resolution windows" (3.1 Continuum emission)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **fit stellar wind mass-loss rate and expansion velocity**: Grid of Monte Carlo CSE radiative transfer models fit by chi2 minimisation to CO spectrum at the star, excluding ISM and spur  
  > "we executed a grid of models over the parameter space and determined the best fit model by $\chi^2$ minimisation to the parts of the spectrum not contaminated with ISM or spur emission" (3.3 The stellar wind)
   - software: Monte Carlo CSE code (Bernes 1979; Schoier & Olofsson 2001)
   - parameter: CO levels up to J=40, ground and first vibrationally excited states  
  > "It incorporates CO rotational energy levels up to J=40 for the vibrational ground state and the first vibrationally excited state" (3.3 The stellar wind)
   - assumption: [CO]/[H2]=1e-4, turbulent velocity 1 km/s, gas-to-dust 40, distance 4 kpc, constant isotropic smooth mass-loss  
  > "assume a \[CO\]/\[H$_2$\] ratio of 10$^{-4}$, a turbulent velocity of 1 $\mathrm{km\,s^{-1}}$, and a gas-to-dust ratio of 40" (3.3 The stellar wind)
   - fitting: chi2 minimisation over grid; errors from 1 sigma chi2 error ellipse  
  > "These errors are the statistical errors corresponding to the 1$\sigma$ $\chi^2$ error ellipse." (3.3 The stellar wind)
   - validation: _not stated_
3. **estimate clump, spur and arc masses**: RADEX grid reproducing average peak clump brightness; CO column to mass assuming spherical clumps  
  > "we used the radiative transfer code RADEX (cite: van-der-Tak:2007aa) to find the range of parameters needed to reproduce the average peak clump brightness in CO 2-1" (3.4 The clumpy CO ring)
   - software: RADEX
   - parameter: linewidth 10 km/s, background 2.73 K, clump diameter 8''  
  > "we fixed the linewidth to 10 $\mathrm{km\,s^{-1}}$ and the background temperature to 2.73 K" (3.4 The clumpy CO ring)
   - assumption: CO abundance 1e-4 vs H2  
  > "a CO abundance of 10$^{-4}$ compared with H$_2$" (3.4 The clumpy CO ring)
   - fitting: _not stated_
   - validation: _not stated_
4. **measure 12CO/13CO ratio in the spur**: Simultaneous fit of APEX 12CO and 13CO spectra with same three-Gaussian profile times a scaling factor  
  > "we fit both spectra simultaneously with the same profile, multiplied by a scaling factor." (3.5 The spur)
   - software: CLASS
   - assumption: 12CO optically thin so ratio equals 12C/13C  
  > "Equating this to the $^{12}$C/$^{13}$C abundance ratio requires the assumption that $^{12}$CO is optically thin." (3.5 The spur)
   - fitting: three Gaussian components; sampler/priors not stated  
  > "The profile was well decomposed into three gaussian components." (3.5 The spur)
   - validation: _not stated_

## Software

- **CASA** : calibration, imaging, uvcontsub  
  > "Data were calibrated and imaged in a standard way using CASA" (2.1 ALMA Compact Array data)
- **RADEX** : CO column density and clump mass  
  > "we used the radiative transfer code RADEX (cite: van-der-Tak:2007aa)" (3.4 The clumpy CO ring)
- **CLASS** : APEX data reduction  
  > "The data were reduced in the standard single-dish data reduction package CLASS" (2.2 APEX data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO expansion velocity | 100 | ±10 | km/s | 2 | We find an expansion velocity of 100$\pm$10 $\mathrm{km\,s^{-1}}$ |
| mass-loss rate | 8e-5 | ±1.5e-5 | Msun/yr | 2 | a mass-loss rate of 8$\pm$1.5 $\times10^{-5}$ M$_\odot$ yr$^{-1}$ |
| H30alpha line centre velocity | 21 | ±3 | km/s | 1 | a gaussian fit finds the line centered on 21$\pm$3 $\mathrm{km\,s^{-1}}$ with a FWHM of 57$\pm$6 $\mathrm{km\,s^{-1}}$ |
| H30alpha FWHM | 57 | ±6 | km/s | 1 | with a FWHM of 57$\pm$6 $\mathrm{km\,s^{-1}}$ |
| continuum flux densities at 215.9 and 231.5 GHz | 42 and 48 | not stated | mJy | 1 | with flux densities of 42 and 48 mJy in the two bands centered on 215.9 and 231.5 GHz, respectively |
| wind gas mass (lower bound) | 0.04 | not stated | Msun | 2 | we can estimate a total gas mass for this stellar wind of 0.04 M$_\odot$ |
| 12CO/13CO intensity ratio in spur | 13 | +10/-5 | dimensionless | 4 | We find a $^{12}$CO/$^{13}$CO intensity ratio of $13^{+10}_{-5}$. |
| spur gas mass | ~3 | not stated | Msun | 3 | corresponding to a gas mass of $\sim$3 M$_\odot$ |
| CO clump mass per clump | 0.03-0.3 | not stated | Msun | 3 | which corresponds to a mass of 0.03-0.3 M$_\odot$ per clump |
| spur peak brightness temperature | 7.8 | not stated | K | 1 | reaches a peak brightness temperature of 7.8 K in the ACA beam |

## Qualitative findings

- CO ring kinematics are not those of an expanding shell, but show a velocity gradient resembling a torus  
  > "the overall kinematics clearly do not reflect that of an expanding shell" (3.4 The clumpy CO ring)

## Claim tuples

- H: Does the CO plateau give the systemic velocity and wind parameters of IRAS 17163? | E: CO 2-1 spectrum at the star fit with Monte Carlo CSE model grid | R: v_sys +18 km/s, v_exp 100±10 km/s, Mdot 8±1.5e-5 Msun/yr | F: A fast, high mass-loss wind, resolving the APEX/optical velocity discrepancy | **supported**
- H: Is the CO ring an expanding shell? | E: Channel maps and velocity map of ring clumps | R: Velocity gradient red to SE, blue to NW | F: Likely a torus ejected by the star, not an expanding shell | **partially**
- H: Is the spur associated with the star? | E: Morphology, velocity, Herschel match and 12CO/13CO ratio | R: Ratio 13 (+10/-5) | F: Spur was ejected by the star in its RSG phase | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Ring as swept-up ISM, and spur as an interstellar cloud (rejected via Larson's law), considered  
  > "Hence, the spur is very unlikely to be a molecular cloud." (4.2 Origin of the spur)
- How they decided it was enough: _not stated_
- Limitation (authors): Wind model made for AGB stars and assumes constant isotropic mass loss; only order-of-magnitude estimate  
  > "this method provides an order of magnitude estimate of the mass-loss rate" (3.3 The stellar wind)
- Limitation (authors): ISM emission and filtering of extended emission (>30'') cause contamination and negative artefacts  
  > "This causes negative artefacts in the data, due to the filtering out of extended emission ($>30''$) by the interferometric observations." (3.2 The interstellar surroundings)
- Caveat (inferred, ours): Mass-loss rate depends on unconstrained model grid and fixed assumptions (distance, CO abundance)
- Caveat (inferred, ours): 12CO/13CO ratio has S/N~4 and uses single-dish APEX data with different beam
- Caveat (inferred, ours): Clump masses rely on unconstrained temperature and density

## Reproducibility

- Data public (paper): ALMA project code given; no explicit public statement  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00502.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Calibration and imaging parameters
- Missing: Model grid specifics and the CSE code configuration
- Missing: Spectral extraction and masking choices
- Data volume (inferred): ~10-50 GB raw ACA mosaic data
- Score (inferred): 3/5, Public ALMA data and clear conceptual recipe, but calibration, imaging and model grid details are sparse.
- Rediscovery candidate: no, Imaging and model setup too underspecified; several results are qualitative or rely on non-ALMA data.

## Links

- Method: (cite: Schoier:2001ab) (Monte Carlo CSE radiative transfer model)
- Method: (cite: van-der-Tak:2007aa) (RADEX)
- Companion: (cite: Wallstrom:2015aa) (Earlier APEX CO observations of IRAS 17163)
- Companion: (cite: Hutsemekers:2013aa) (Herschel dust shell)

## Checks

```json
{
 "quotes": 64,
 "quotes_ok": 64,
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
  "facts": 74,
  "stated": 41,
  "rate": 0.554
 },
 "evidence_ok": true
}
```
