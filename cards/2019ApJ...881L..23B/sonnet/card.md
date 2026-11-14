# The z = 7.54 Quasar ULAS J1342+0928 Is Hosted by a Galaxy Merger

`2019ApJ...881L..23B` | The Astrophysical Journal Letters 2019 | first author: Bañados, Eduardo | arXiv: 1909.00027 | DOI: 10.3847/2041-8213/ab3659

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: What are the morphology and kinematics of the [C II] and dust emission in the host galaxy of the z=7.54 quasar J1342+0928, and is it consistent with a simple rotating disk?  
  > "Here we test whether our current data can rule out a simple rotating disk." (Rotating disk model)
- Target **ULAS J1342+0928**: coordinates 13h42m08.098s +09d28m38.35s (ICRS, continuum peak)  
  > "The peak of the continuum emission at $13^{\rm h} 42^{\rm m} 08.098s$ $+09^{\circ} 28^{\prime} 38.35\ensuremath{''}$ (ICRS)" (Results and discussion); "the redshift of the quasar, $z=7.5413$, measured from NOEMA data (cite: venemans2017c)" (Observations); z/distance z = 7.5413  
  > "The peak of the continuum emission at $13^{\rm h} 42^{\rm m} 08.098s$ $+09^{\circ} 28^{\prime} 38.35\ensuremath{''}$ (ICRS)" (Results and discussion); "the redshift of the quasar, $z=7.5413$, measured from NOEMA data (cite: venemans2017c)" (Observations); distance from NOEMA [C II] (Venemans et al. 2017b)  
  > "The peak of the continuum emission at $13^{\rm h} 42^{\rm m} 08.098s$ $+09^{\circ} 28^{\prime} 38.35\ensuremath{''}$ (ICRS)" (Results and discussion); "the redshift of the quasar, $z=7.5413$, measured from NOEMA data (cite: venemans2017c)" (Observations)

## Data provenance

- ALMA projects: 2017.1.00396.S
- bands: Band 6  
  > "We performed ALMA Band 6 observations to spatially resolve the \[C II\] line of J1342+0928." (Observations)
- frequencies and spectral setup: tuned to 222.511 GHz ([C II] at z=7.5413)  
  > "The observations were tuned to cover 222.511 GHz" (Observations)
- continuum bandwidth: 6.6 GHz effective (line-free channels), 231.5 GHz  
  > "We imaged the line-free channels (effective bandwidth of 6.6 GHz) to create the dust continuum map at 231.5 GHz" (Continuum and [C II] maps)
- arrays: _not stated_
- configurations: C43-6  
  > "The observations were carried out on 2017 December 26 in the C43-6 array with a total on-source time of 114 minutes." (Observations)
- baselines: _not stated_
- angular resolution: 0.28" x 0.20" (1.4 x 1.0 kpc)  
  > "We present ALMA $0.28\ensuremath{''} \times 0.20\ensuremath{''}$ ($1.4\,\mathrm{kpc} \times 1.0\,\mathrm{kpc}$) resolution observations" (abstract)
- max recoverable scale: 3"  
  > "the maximum recoverable scale[^5] of our observations is 3$\ensuremath{''}$" (Observations)
- sensitivity: 0.1 mJy/beam per 50 km/s channel; 0.07 mJy/beam per 100 km/s; continuum 7.7 uJy/beam  
  > "an rms noise level of 0.1 mJy beam$^{-1}$ for each channel" (Observations); "yielding an rms value of 7.7 $\mu$Jy beam$^{-1}$ in the final map" (Observations)
- time on source: 114 minutes  
  > "in the C43-6 array with a total on-source time of 114 minutes" (Observations)
- observing dates: 2017 December 26  
  > "The observations were carried out on 2017 December 26" (Observations)
- pi or archival as stated: _not stated_
- Line: [C II] 158 um fine-structure (1900.5369 GHz)
- Other facility **IRAM/NOEMA**: Low-resolution [C II] detection and redshift z=7.5413  
  > "IRAM/NOEMA observations resulted in the detection of the \[C II\] line and dust from this quasar at $z=7.5413\pm0.0007$" (Introduction)
- External data: NOEMA redshift and [C II] FWHM used to set line width for moment-0 map  
  > "This width corresponds to the 1.2$\times$FWHM measured in the low-resolution NOEMA data (cite: venemans2017c)" (Continuum and [C II] maps) [from (cite: venemans2017c)]

## Processing

### Calibration

- pipeline or manual: Default ALMA calibration pipeline in CASA  
  > "We used the default ALMA calibration pipeline implemented in the Common Astronomy Software Application package (cite: mcmullin2007) to calibrate the dataset[^6]." (Observations)
- casa version: CASA 5.4.0-68 (imaging)  
  > "CASA version 5.4.0-68" (footnote 7)
- pipeline version: CASA calibration pipeline 5.1.1-5  
  > "CASA calibration pipeline version 5.1.1-5" (footnote 6)
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean  
  > "Visibilities were imaged with the tclean[^7] task using natural weighting" (Observations)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "using natural weighting to maximize the signal-to-noise (S/N) of our detection" (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: clean to 2 sigma inside circle of 2" radius at source  
  > "cleaning was performed down to $2\sigma$ inside a circle with a radius of $2\ensuremath{''}$ centered at the source" (Observations)
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub  
  > "The continuum was subtracted from visibilities with the task uvcontsub" (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.28" x 0.20"  
  > "synthesized beam of $0.28\ensuremath{''} \times 0.20\ensuremath{''}$" (Observations)
- final rms: 0.1 mJy/beam per 50 km/s channel  
  > "an rms noise level of 0.1 mJy beam$^{-1}$ for each channel" (Observations)

### Inherited from earlier work

- Residual scaling method for flux measurement  
  > "see Appendix A in (cite: novak2019); and also (cite: jorsater1995; walter1999) for further details" ([C II] spectrum) [from (cite: novak2019); (cite: jorsater1995; walter1999)]
- Thin tilted disk model with exponential profile  
  > "as described in Section 4 of (cite: venemans2019) and in Appendix C of (cite: neeleman2019)" (Rotating disk model) [from (cite: venemans2019); (cite: neeleman2019)]
- Dynamical mass formula  
  > "$M_{\rm dyn}/M_\odot=1.16\times 10^5\,v_{\rm circ}^2\,D$ (cite: wang2013)" (Rotating disk model) [from (cite: wang2013)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges for continuum and uvcontsub fit order
- Cell size and image size
- Disk model priors, MCMC sampler and code
- Which data were used for the disk fit (cube channel width, masks)
- Definition of source sizes (how 3.2x6.4 kpc measured)

## Analysis recipe

1. **Calibrate and image**: Default pipeline calibration; tclean natural weighting; uvcontsub; cubes at 50 and 100 km/s and continuum map  
  > "Visibilities were imaged with the tclean[^7] task using natural weighting to maximize the signal-to-noise (S/N) of our detection" (Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract [C II] spectrum and fit**: 1.3" radius aperture on dirty map scaled by clean-to-dirty beam area ratio, Gaussian fit  
  > "The correct flux measurement is equal to $\epsilon\times D$, where $\epsilon=C / (D - R)$ is the clean-to-dirty beam area ratio" ([C II] spectrum)
   - software: CASA
   - parameter: epsilon = 0.4; aperture radius 1.3"  
  > "and in our case is $\epsilon=0.4$" ([C II] spectrum)
   - fitting: Gaussian fit  
  > "a Gaussian fit results in the integrated \[C II\] line flux of $1.22\pm 0.15$ Jy km s$^{-1}$" ([C II] spectrum)
   - validation: Compared with NOEMA spectrum  
  > "The agreement between our ALMA spectrum and the low-resolution ($\sim$$2\ensuremath{''}$) NOEMA spectrum" ([C II] spectrum)
3. **Fit thin rotating disk model**: Exponential thin tilted disk with constant vcirc and dispersion, chi2 minimization via MCMC  
  > "We obtain the best fit and uncertainties of the parameters performing a $\chi^2$ minimization using a Markov Chain Monte Carlo approach." (Rotating disk model)
   - fitting: chi2 minimization with MCMC; priors not stated  
  > "performing a $\chi^2$ minimization using a Markov Chain Monte Carlo approach" (Rotating disk model)
   - validation: Residuals in moment-0 and channel maps show +-2 sigma structure, >4 sigma in one channel  
  > "There are $\pm 2\sigma$ residuals in all channel maps" (Rotating disk model)
4. **Dynamical mass**: Mdyn = 1.16e5 vcirc^2 D  
  > "$M_{\rm dyn}/M_\odot=1.16\times 10^5\,v_{\rm circ}^2\,D$ (cite: wang2013)" (Rotating disk model)
   - parameter: vcirc=57 km/s, D=6.4 kpc  
  > "Using the numbers from our best-fit model ($v_{\rm circ}=57\,{\rm km\,s}\ensuremath{^{-1}}$ and $D=6.4\,$kpc)" (Rotating disk model)
   - assumption: Thin rotating disk geometry  
  > "In the case of a rotating thin disk geometry" (Rotating disk model)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.4.0-68 (pipeline 5.1.1-5): Calibration, tclean, uvcontsub  
  > "We used the default ALMA calibration pipeline implemented in the Common Astronomy Software Application package" (Observations)
- **Astropy** : listed in software  
  > "Astropy (cite: astropy2018), CASA (cite: mcmullin2007), Matplotlib (cite: hunter2007)" (Software)
- **Matplotlib** : listed in software  
  > "Astropy (cite: astropy2018), CASA (cite: mcmullin2007), Matplotlib (cite: hunter2007)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| [C II] integrated line flux | 1.22 | 0.15 | Jy km/s | 2 | integrated \[C II\] line flux of $1.22\pm 0.15$ Jy km s$^{-1}$ |
| [C II] FWHM | 318 | 29 | km/s | 2 | FWHM of $318 \pm 29$ km s$^{-1}$ |
| [C II] redshift | 7.5400 | 0.0003 | dimensionless | 2 | a redshift of $7.5400 \pm 0.0003$ |
| Continuum flux density at 231.5 GHz | 0.39 | 0.07 | mJy | 1 | we measure a flux density of $0.39\pm 0.07$ mJy in a circular aperture of radius $1.3\ensuremath{''}$ |
| Mg II blueshift relative to [C II] | 456 | 140 | km/s | 2 | blueshifted by $456\pm 140\,{\rm km\,s}\ensuremath{^{-1}}$ |
| Disk circular velocity | 57 | 14 | km/s | 3 | $v_{\rm circ}=57 \pm 14\,{\rm km\,s}\ensuremath{^{-1}}$ |
| Velocity dispersion | 134 | 8 | km/s | 3 | a velocity dispersion $\sigma_v = 134\pm8\,{\rm km\,s}\ensuremath{^{-1}}$ |
| Inclination | 56 | +4/-6 | deg | 3 | $i=56^\circ$$^{+4^\circ}_{-6^\circ}$ |
| Dynamical mass | 2.4e9 | not stated | Msun | 4 | it yields a very small dynamical mass of $M_{\rm dyn}=2.4\times 10^9\,M_\odot$ |

## Qualitative findings

- [C II] is ~1.5 times more extended than the continuum with two separate peaks  
  > "The \[C II\] line is $\sim$1.5 times more extended than the continuum emission" (abstract)

## Claim tuples

- H: Is the [C II] host consistent with a coherent rotating disk? | E: Moment maps, channel maps and thin disk MCMC fit | R: vcirc=57 km/s, sigma=134 km/s, significant channel residuals | F: Chaotic motion reminiscent of an ongoing merger; no evidence for coherent rotation | **supported**
- H: Is the host compact and featureless as predicted by BlueTides? | E: Compare ALMA maps with simulation predictions | R: Extended complex host; [C II] within +-180 km/s, no strong outflow | F: Data differ from BlueTides predictions | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Higher S/N and resolution needed for narrower channel maps and clumpiness  
  > "Higher S/N observations are required to reveal more details in narrower \[C II\] channel maps" (Kinematics: Channel maps)
- Caveat (inferred, ours): Disk fit with sigma>vcirc and low S/N is poorly constrained; merger interpretation is qualitative
- Caveat (inferred, ours): Dynamical mass depends on assumed D and inclination treatment

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: MCMC disk model code and priors
- Missing: line-free channel selection
- Missing: cell/image size
- Data volume (inferred): ~20-50 GB (single Band 6 C43-6 execution)
- Score (inferred): 3/5, Data identified and imaging fairly described, but disk fit details are inherited or missing.
- Rediscovery candidate: no, Disk-model fitting details and imaging parameters are incomplete.

## Links

- Method: (cite: venemans2019); (cite: neeleman2019) (Disk model)
- Method: (cite: novak2019) (Residual scaling flux method)
- Companion: (cite: novak2019) (Multiline ALMA survey of the same quasar host)

## Checks

```json
{
 "quotes": 61,
 "quotes_ok": 61,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 68,
  "stated": 43,
  "rate": 0.632
 },
 "evidence_ok": true
}
```
