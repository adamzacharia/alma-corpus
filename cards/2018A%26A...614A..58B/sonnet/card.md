# High-resolution observations of IRAS 08544-4431. Detection of a disk orbiting a post-AGB star and of a slow disk wind

`2018A&A...614A..58B` | Astronomy and Astrophysics 2018 | first author: Bujarrabal, V. | arXiv: 1802.04019 | DOI: 10.1051/0004-6361/201732422

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars, stellar_physics
- Question: Does the post-AGB binary IRAS 08544-4431 host a rotating Keplerian disk plus a slow outflow, and what are their structure, mass, dynamics and angular momentum?  
  > "Our observations reveal the presence of an equatorial disk in rotation; a low-velocity outflow is also found, probably formed of gas expelled from the disk." (abstract)
- Target **IRAS 08544-4431**: coordinates RA 08:56:14.165, Dec -44:43:10.588 (continuum center)  
  > "Dust continuum emission was found to be not resolved and centered at RA 08:56:14.165  DEC $-$44:43:10.588" (Observations); "As we see later in this work, $D$ $\sim$ 1100 pc is more compatible with our estimates of the total stellar mass, and we have adopted this value" (Introduction); z/distance 1100 pc adopted (550 pc alternative)  
  > "Dust continuum emission was found to be not resolved and centered at RA 08:56:14.165  DEC $-$44:43:10.588" (Observations); "As we see later in this work, $D$ $\sim$ 1100 pc is more compatible with our estimates of the total stellar mass, and we have adopted this value" (Introduction); distance from Adopted from compatibility with stellar mass estimates; Gaia parallax 0.86 +/- 0.6 mas judged inaccurate; 550 pc from earlier assumed luminosity  
  > "Dust continuum emission was found to be not resolved and centered at RA 08:56:14.165  DEC $-$44:43:10.588" (Observations); "As we see later in this work, $D$ $\sim$ 1100 pc is more compatible with our estimates of the total stellar mass, and we have adopted this value" (Introduction)

## Data provenance

- ALMA projects: 2013.1.00338.S
- bands: Band 7 (0.8 mm)  
  > "$\lambda$ = 0.8 mm that were obtained with ALMA, band 7 receiver." (Observations)
- frequencies and spectral setup: spectral resolution ~0.2 km/s; delivered channel 0.11 km/s; degraded to ~0.43 km/s for maps  
  > "the data were delivered with a channel spacing of 0.11 km s$^{-1}$)." (Observations); "the resolution was degraded to about 0.43 km s$^{-1}$ to improve the S/N at high velocities." (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15 to 2483 m, 34 antennas  
  > "Thirty-four antennas were used with baselines ranging from 15 to 2483 m." (Observations)
- angular resolution: 0.19x0.18 arcsec (natural), 0.13x0.10 arcsec (robust)  
  > "which leads to channel maps with 0.19$\times$0.18 arcsec and 0.13$\times$0.10 arcsec (HPBW) resolutions, respectively." (Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: ~37 min per track, five tracks  
  > "The source was observed for $\sim$ 37 min in each track." (Observations)
- observing dates: Three runs Aug 29-30 2015, two runs Aug 25 and Sep 3 2016  
  > "three between August 29 and 30, 2015, and two more in August 25 and September 3, 2016." (Observations)
- pi or archival as stated: _not stated_
- Line: 12CO J=3-2 (not stated)
- Line: 13CO J=3-2 (not stated)
- Other facility **APEX**: Single-dish 12CO 3-2 profiles used to estimate flux loss  
  > "By comparing our data with APEX single-dish profiles (Bujarrabal et al. 2013a), we conclude that a small fraction of the flux, $<$ 20%, was filtered out" (Observations)
- External data: APEX single-dish CO profiles and earlier mass estimate  
  > "APEX single-dish profiles (Bujarrabal et al. 2013a)" (Observations) [from Bujarrabal et al. 2013a]
- External data: Binary orbit parameters / mass function  
  > "IRAS 08544$-$4431 is a double stellar system; see Van Winckel et al. (2009)." (Introduction) [from Van Winckel et al. (2009)]
- External data: VLTI inner rim diameter ~15 mas and inclination ~20 deg  
  > "The inner rim of the disk was imaged, showing a diameter of about 15 mas and suggesting an inclination with respect to the plane of the sky of about 20$^\circ$." (Introduction) [from Hillen et al. 2016]
- External data: Core-mass luminosity relation  
  > "Using the core-mass luminosity relation of Miller Bertolami (2016), this results in a post-AGB mass of about 0.65 M$_{\odot}$." (3.1 Description of the best-fit model) [from Miller Bertolami (2016)]

## Processing

### Calibration

- pipeline or manual: Calibrated with CASA (details not given)  
  > "Data were calibrated with the CASA software package." (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Quasars J0538-4405, J0922-3959, J0904-5735 for bandpass, flux and phase  
  > "The quasars J0538-4405, J0922-3959, and J0904-5735 were observed for bandpass, flux, and phase calibrations." (Observations)
- flux scale uncertainty: No extra rescaling; <20% flux filtered out in 12CO vs APEX  
  > "the flux calibration was judged to be optimal and no additional flux rescaling was applied." (Observations)
- self calibration: Additional phase self-calibration on compact continuum source (GILDAS)  
  > "First, additional phase self-calibration was performed using the compact continuum source as reference." (Observations)

### Imaging

- task: GILDAS imaging and deconvolution  
  > "After the data calibration, the rest of the analysis was made with the GILDAS software package." (Observations)
- deconvolver: Hogbom and SDI tried; SDI used for final data  
  > "The data here presented were obtained with natural weighting and SDI method." (Observations)
- weighting robust: Natural (adopted) and robust (value not given)  
  > "Image deconvolution was carried out with natural and also robust weighting" (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Continuum (~320 mJy, uv-plane fit) subtracted from maps  
  > "Such a continuum level was subtracted from our maps to better show the weakest features" (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Velocity resolution degraded to ~0.43 km/s (full resolution for PV diagrams)  
  > "We kept however the highest spectral resolution for the position-velocity diagrams" (Observations)
- final beam: 0.19x0.18 arcsec for natural weighting  
  > "channel maps with 0.19$\times$0.18 arcsec and 0.13$\times$0.10 arcsec (HPBW) resolutions" (Observations)
- final rms: _not stated_

### Inherited from earlier work

- Nebula model codes and general model patterns  
  > "We used codes that are very similar to those described in our previous works (Bujarrabal et al. 2013b, 2015, 2017, ...)." (3 Modeling of our ALMA maps) [from Bujarrabal et al. 2013b, 2015, 2017]
- CO abundances and 12CO/13CO = 10 adopted as in previous works  
  > "Also following those works, we adopted an abundance ratio $^{12}$CO/$^{13}$CO = 10." (3.1 Description of the best-fit model) [from Bujarrabal et al. previous works]

### Not stated but needed to reproduce (our reading)

- Robust weighting parameter value
- SDI clean parameters, masks, and number of iterations
- CASA version and calibration script
- Spectral window rest frequencies
- Fitting procedure and merit function for model comparison (apparently by eye)
- Code for the radiative transfer model not released
- Which calibrator served which role
- Self-calibration solution intervals

## Analysis recipe

1. **Calibrate and image data**: CASA calibration, GILDAS phase self-cal, SDI CLEAN with natural weighting, continuum subtraction  
  > "The data here presented were obtained with natural weighting and SDI method." (Observations)
   - software: CASA, GILDAS
   - parameter: Channels degraded to 0.43 km/s  
  > "the resolution was degraded to about 0.43 km s$^{-1}$ to improve the S/N at high velocities." (Observations)
   - fitting: _not stated_
   - validation: Flux compared with APEX profiles; <20% flux lost  
  > "a small fraction of the flux, $<$ 20%, was filtered out in the maps of $^{12}$CO $J$=3$-$2." (Observations)
2. **Model nebula with LTE radiative transfer**: Axisymmetric disk (inner Keplerian, outer sub-Keplerian + expansion) plus outflow; LTE radiative transfer on ~10^6 cells and 10^4-10^5 rays, convolved with clean beam, compared with maps and PV diagrams  
  > "Typically, we solve the transfer equations following 10$^4$ to 10$^5$ rays, which traverse the cells in which the nebula has been divided." (3 Modeling of our ALMA maps)
   - parameter: Inclination 70 deg to plane of sky axis, PA -15 deg, X(13CO)=1.5e-5, X(12CO)=1.5e-4  
  > "| Axis inclination with respect to the plane of the sky |  | 70$^\circ$ | from IR and CO data |" (Table 1)
   - assumption: LTE level populations, constant abundances, axial symmetry, D = 1100 pc  
  > "We assume local-thermal-equilibrium (LTE) populations for the involved rotational levels." (3 Modeling of our ALMA maps)
   - fitting: Manual exploration of many configurations; best-fit model chosen by comparison with data and previous results, no formal sampler  
  > "In any case, a high number of different configurations were analyzed." (3 Modeling of our ALMA maps)
   - validation: Comparison of predicted channel maps and PV diagrams with data; similarity to Red Rectangle, IW Car  
  > "comparing the predictions with the observational data and other previous results; see predicted maps per velocity channel and position-velocity diagram in Figs. 3 and 5." (3.1 Description of the best-fit model)
3. **Derive masses, lifetime, angular momentum and distance scaling**: Integrate density and velocity laws for mass and angular momentum; disk lifetime from disk/outflow mass ratio and outflow formation time; scaling with D tested  
  > "We derived the disk angular momentum by integrating the local momentum of the volume units for the adopted density and velocity laws." (3.1 Description of the best-fit model)
   - assumption: Outflow gas expelled from disk; gas ejected with negligible rotation  
  > "assuming, as we deduced for similar sources (Sect. 1), that the outflowing gas has been expelled from the disk" (3.1 Description of the best-fit model)
   - fitting: _not stated_
   - validation: Uncertainties estimated analytically from abundance range and velocity errors  
  > "We so expect a moderate uncertainty in the estimate of the molecule-rich gas mass, $\sim$ $\pm$50%." (3.2 Uncertainties)

## Software

- **CASA** : Data calibration  
  > "Data were calibrated with the CASA software package." (Observations)
- **GILDAS** : Self-calibration, imaging, deconvolution and analysis  
  > "After the data calibration, the rest of the analysis was made with the GILDAS software package." (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total central mass (D=1100 pc) | 1.8 | ~40% | Msun | 2 | The disk rotation indicates a total central mass of about 1.8 $M_{\mbox{\ensuremath{\odot}}}$, for a distance of 1100 pc.; We estimate that the stellar mass uncertainty is of about 40%. |
| Total nebular mass | ~2e-2 | ~50% | Msun | 3 | The total nebular mass is $\sim$ 2 10$^{-2}$ $M_{\mbox{\ensuremath{\odot}}}$, of which $\sim$ 90% corresponds to the disk. |
| Disk lifetime | ~10000 | 5000 to 2e4 yr | yr | 3 | we derive a disk lifetime of $\sim$ 10000 yr. |
| Disk angular momentum (1100 pc) | ~13 | not stated | Msun km/s AU | 3 | yields a high value $J$ $\sim$ 13 $M_{\mbox{\ensuremath{\odot}}}$ km s$^{-1}$ AU for our best distance estimate |
| Continuum flux | ~320 | 1 | mJy | 1 | yielded a total flux of $\sim$ 320 $\pm$ 1 mJy |
| Outflow formation timescale | ~1100 | not stated | yr | 3 | we derived a typical time required to form it of about 1100 yr. |

## Qualitative findings

- Equatorial Keplerian disk (inner) with sub-Keplerian expanding outer disk and slow X-shaped outflow  
  > "Our maps of IRAS 08544$-$4431 also show a clearly composite nebula with a disk in rotation and gas in expansion." (Conclusions)

## Claim tuples

- H: IRAS 08544-4431 hosts a rotating disk and slow outflow like other NIR-excess post-AGB stars | E: ALMA 12CO/13CO 3-2 maps and LTE nebula modeling | R: Rotation plus expansion reproduced, central mass 1.8 Msun, nebular mass 2e-2 Msun | F: Composite nebula confirmed, similar to the Red Rectangle | **supported**
- H: Distance of 1100 pc versus 550 pc | E: Compare total mass from rotation with binary orbit parameters | R: 550 pc gives ~1 Msun total and 0.1 Msun primary | F: Favors ~1100 pc though uncertain | **partially**
- H: Disk angular momentum came from the binary, shrinking the orbit | E: Compare disk J (~13) with binary J (~20) | R: Past binary J ~33 | F: Orbit decreased by factor ~2 | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Data and knowledge moderate, so simple models following those of better studied objects  
  > "very detailed models, such as those developed for the Red Rectangle, are not sensible" (3 Modeling of our ALMA maps)
- Alternative: Distance 550 pc considered; purely radial velocity field cannot be ruled out  
  > "we cannot rule out a purely radial velocity (as found for IW Car)." (3.2 Uncertainties)
- How they decided it was enough: _not stated_
- Limitation (authors): Inner disk and width poorly constrained; mass depends on CO abundance and distance; LTE assumption; temperature uncertain  
  > "Some disk properties are not well determined from the observations, mainly because of the relatively low angular resolution" (3.2 Uncertainties)
- Caveat (inferred, ours): Model fit is by eye, no goodness-of-fit or parameter posteriors
- Caveat (inferred, ours): Distance choice drives mass, J and lifetime scalings (D, D^2, D^3)
- Caveat (inferred, ours): Abundance-density degeneracy under LTE
- Caveat (inferred, ours): Calibrator flux changed between years

## Reproducibility

- Data public (paper): Project code given; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00338.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Radiative transfer model code
- Missing: Exact imaging parameters
- Missing: Fitting criteria
- Data volume (inferred): ~50-200 GB raw for five Band 7 tracks
- Score (inferred): 3/5, Data identifiable but modeling code is unreleased and fit is manual with few stated criteria.
- Rediscovery candidate: no, The model code is not available and the fit is not an objective recipe.

## Links

- Method: Bujarrabal et al. 2013b, 2015, 2017 (Model code and approach for Red Rectangle, AC Her and IW Car)
- Companion: Bujarrabal et al. 2013a (APEX single-dish CO survey of NIR-excess post-AGB stars)

## Checks

```json
{
 "quotes": 63,
 "quotes_ok": 63,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 68,
  "stated": 45,
  "rate": 0.662
 },
 "evidence_ok": true
}
```
