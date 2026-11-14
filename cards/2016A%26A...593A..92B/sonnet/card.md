# Further ALMA observations and detailed modeling of the Red Rectangle

`2016A&A...593A..92B` | Astronomy and Astrophysics 2016 | first author: Bujarrabal, V. | arXiv: 1606.07238 | DOI: 10.1051/0004-6361/201628546

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars
- Question: What are the properties of the rotating disk and the expanding outflow in the Red Rectangle post-AGB nebula, and how are they related?  
  > "We aim to study the rotating and expanding gas in the Red Rectangle, which is a well known object that recently left the asymptotic giant branch (AGB) phase." (abstract)
- Target **Red Rectangle**: coordinates _not stated_; z/distance 710 pc  
  > "Men’shchikov et al. deduced a distance of 710 pc for this source, which is compatible with our previous analysis of CO data." (1 Introduction); distance from Men’shchikov et al. (2002)  
  > "Men’shchikov et al. deduced a distance of 710 pc for this source, which is compatible with our previous analysis of CO data." (1 Introduction)

## Data provenance

- ALMA projects: 2011.0.00223.S
- bands: Band 7 and Band 9  
  > "We observed the Red Rectangle with ALMA[^1] using receiver bands 7 and 9 in October-November 2012." (2.1 New ALMA observations and new reduction of the $^{13}$CO $J$=3$-$2 maps)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: Cycle-0 observations  
  > "particularly in these Cycle-0 observations" (2.3 Flux lost by interferometric over-resolution)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Band 7 HPBW ~0.59x0.56 arcsec (natural weighting); Band 9 ~0.31x0.25 arcsec  
  > "A HPBW resolution of $\sim$ 0$''$31$\times$0$''$25 was obtained in band 9." (2.1 New ALMA observations and new reduction of the $^{13}$CO $J$=3$-$2 maps)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: October-November 2012  
  > "We observed the Red Rectangle with ALMA[^1] using receiver bands 7 and 9 in October-November 2012." (2.1 New ALMA observations and new reduction of the $^{13}$CO $J$=3$-$2 maps)
- pi or archival as stated: _not stated_
- Line: C17O J=6-5 (not stated)
- Line: H13CN J=4-3 (not stated)
- Line: 13CO J=3-2 (not stated)
- Line: 12CO J=6-5 and J=3-2 (published maps) (not stated)
- Other facility **Herschel/HIFI**: CI J=1-0, CI J=2-1 and CII J=2-1 spectra; 12CO J=6-5 single-dish profile  
  > "The HIFI heterodyne spectrometer on board the Herschel Space Telescope (Pilbratt et al. 2010; de Graauw et al. 2010) was used to observe three carbon transitions." (2.2 Herschel/HIFI observations of atomic lines in the Red Rectangle)
- Other facility **HST**: Optical image for comparison with ALMA maps  
  > "In these figures we also show a Hubble Space Telescope (HST) optical image" (2.1 New ALMA observations and new reduction of the $^{13}$CO $J$=3$-$2 maps)
- Other facility **IRAM 30m**: Single-dish CO profiles used in the fitting  
  > "These observations were obtained with the 30 m IRAM radio telescope and Herschel/HIFI" (5.2 Fitting of single-dish observations of CO emission)
- External data: Single-dish 12CO and 13CO profiles (IRAM 30m, Herschel/HIFI) fitted by the model  
  > "We also reproduced the $^{12}$CO and $^{13}$CO single-dish profiles presented in Bujarrabal & Alcolea (2013)." (5 Model fitting) [from Bujarrabal & Alcolea (2013)]
- External data: Previously published 12CO J=3-2 and J=6-5 ALMA maps  
  > "$^{12}$CO $J$=3$-$2 and $J$=6$-$5 (Figs. 1 and 3 of Bujarrabal et al. 2013b and Fig. [14](#map65))" (5 Model fitting) [from Bujarrabal et al. (2013b)]
- External data: Distance 710 pc  
  > "Men’shchikov et al. deduced a distance of 710 pc for this source" (1 Introduction) [from Men’shchikov et al. (2002)]
- External data: Collisional rates from LAMBDA  
  > "collisional rates were taken from the LAMBDA database" (3 Line emission model) [from LAMBDA database]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting for band 9, H13CN and new 13CO reduction  
  > "In band 9 data and the maps of the weak H$^{13}$CN line, we used natural weighting to improve the mapping quality." (2.1 New ALMA observations and new reduction of the $^{13}$CO $J$=3$-$2 maps)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum subtracted from all channel maps  
  > "the continuum emission was subtracted from all the channel maps here presented." (2.1 New ALMA observations and new reduction of the $^{13}$CO $J$=3$-$2 maps)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: 13CO spectral resolution degraded to 0.66 km/s  
  > "degrading the spectral resolution to 0.66 km s$^{-1}$" (4 Observational results from our ALMA maps)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- ALMA observation details and data reduction  
  > "Details on the observations and data reduction can be found in Bujarrabal et al. (2013b)." (2.1 New ALMA observations and new reduction of the $^{13}$CO $J$=3$-$2 maps) [from Bujarrabal et al. (2013b)]
- Radiative transfer code and its tests  
  > "The code was first presented in Bujarrabal & Alcolea (2013), which includes the details of the numerical treatment and exhaustive tests of the calculation accuracy" (3 Line emission model) [from Bujarrabal & Alcolea (2013)]
- Beam convolution and synthetic map calculation  
  > "The beam convolution and calculation of synthetic maps are similar to those shown in Bujarrabal et al. (2013b)." (3 Line emission model) [from Bujarrabal et al. (2013b)]
- HIFI calibration to Tmb and flux units  
  > "later converted into main-beam temperatures (T$_\mathrm{mb}$) and flux units; see more details in, for example, Alcolea et al. (2013)." (2.2 Herschel/HIFI observations of atomic lines in the Red Rectangle) [from Alcolea et al. (2013)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration/flagging details (deferred to the 2013 paper)
- Exact channel widths, line-free channels and continuum fitting order
- Image size and cell size, clean thresholds and masks
- Rest frequencies of the ALMA lines
- The radiative transfer code is not publicly available
- Model grid, number of cells and iteration convergence criteria
- Source coordinates
- Quantitative goodness-of-fit metric (fit done by inspection)

## Analysis recipe

1. **Re-image 13CO and image new lines**: New image synthesis with natural weighting, continuum subtracted, 13CO spectral resolution 0.66 km/s  
  > "we performed a new image synthesis of those data, assuming natural weighting of the visibilities (which yields a wider beam and a better sensitivity) and degrading the spectral resolution to 0.66 km s$^{-1}$" (4 Observational results from our ALMA maps)
   - fitting: _not stated_
   - validation: _not stated_
2. **Estimate flux lost to interferometric filtering**: Compare angle-integrated 12CO J=6-5 ALMA flux profile with Herschel/HIFI single-dish profile  
  > "the flux recovered by the ALMA maps is typically about 60–70% of the total flux" (2.3 Flux lost by interferometric over-resolution)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit a 2D nonlocal radiative transfer model to maps and single-dish profiles**: Parametric 2D axisymmetric disk plus outflow model, level populations and radiative transfer solved simultaneously, convolved with the interferometric beam to compare synthetic and observed maps  
  > "Here, the brightness distribution is convolved with the interferometric beam to obtain synthetic maps directly comparable to the observed maps." (3 Line emission model)
   - software: custom nonlocal radiative transfer code, LAMBDA
   - parameter: Distance 710 pc, axis inclination 5 deg from plane of sky, PA 12.5 deg  
  > "Distance |  | 710 pc | various arguments (Sect. 1)" (Table 1)
   - assumption: H13CN hyperfine structure neglected; H13CN uses the same physical conditions as CO  
  > "In the treatment of the H$^{13}$CN line excitation, we do not include the hyperfine structure of the rotational levels." (3 Line emission model)
   - fitting: Fit done by inspection of many predictions, with a free scale factor on single-dish predictions for calibration uncertainty; no formal sampler  
  > "our fitting is just performed by inspection of a high number of predictions and adoption of a solution that is compatible with all observations" (5.4 Uncertainties in the model fitting)
   - validation: Compromise between fitting maps and single-dish profiles; tests with a density increase in the inner disk (App. B)  
  > "we try to fit both the total intensity obtained from single-dish data and the maps" (5 Model fitting)
4. **Derive masses, angular momentum and disk lifetime**: Integrate model density; estimate disk lifetime from mass divided by mass-loss rate to the outflow  
  > "Therefore, the (future) lifetime of the disk derived at this typical distance is $t_{\rm disk}$ $\sim$ 8000 yr." (7 Discussion and conclusions)
   - assumption: Outflow gas comes from the disk; mass-loss rate constant  
  > "If the mass-loss rate from the disk does not significantly vary during the post-AGB phases, we can expect a total disk lifetime of about 7000 yr" (7 Discussion and conclusions)
   - fitting: _not stated_
   - validation: Uncertainty by varying parameters until predictions are incompatible with data (about 50% on density and abundance, 30% on temperature)  
  > "We conclude (and quantitative calculations confirm this result) that 50% is a reasonable limit to the uncertainty of our estimates of the overall density and abundance distributions." (5.4 Uncertainties in the model fitting)

## Software

- **HIPE** : Reduction of Herschel/HIFI data  
  > "We reduced the data with the standard HIFI pipeline in the HIPE software" (2.2 Herschel/HIFI observations of atomic lines in the Red Rectangle)
- **CLASS** : Inspection and averaging of HIFI spectra  
  > "The spectra were then exported to CLASS using the hiClass tool within HIPE" (2.2 Herschel/HIFI observations of atomic lines in the Red Rectangle)
- **LAMBDA database** : Collisional rates  
  > "collisional rates were taken from the LAMBDA database" (3 Line emission model)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Disk mass | 1.3e-2 | about 50% (density/abundance) | Msun | 4 | we find a total disk mass of $\sim$ 1.3 10$^{-2}$ $M_{\mbox{\ensuremath{\odot}}}$. |
| Outflow mass | 1.2e-3 | not stated | Msun | 4 | The mass of the outflow is found to be $\sim$ 1.2 10$^{-3}$ $M_{\mbox{\ensuremath{\odot}}}$. |
| 12CO abundance | 1.2e-4 | not stated | dimensionless | 3 | $X$($^{12}$CO) $\sim$ 1.2 10$^{-4}$ and $X$($^{13}$CO) $\sim$ 1.2 10$^{-5}$ |
| H13CN abundance within 60 AU | 1e-9 | factor ~2 | dimensionless | 3 | $X$(H$^{13}$CN) $\sim$ 10$^{-9}$ only in regions closer than 60 AU |
| Disk angular momentum | 9.1 | not stated | Msun AU km/s | 4 | 2.7 10$^{52}$ g cm$^2$ s$^{-1}$, i.e. $\sim$ 9.1 $M_{\mbox{\ensuremath{\odot}}}$ AU km s$^{-1}$ |
| Disk lifetime | ~8000 (outer/typical), ~10000 inner | not stated | yr | 4 | We therefore deduce a typical lifetime of the Red Rectangle disk $t_{\rm disk}$ $\sim$ 8000 yr, probably $\sim$ 10000 yr for the inner disk regions. |
| ALMA flux recovery for 12CO J=6-5 | 60-70 | not stated | percent | 2 | the flux recovered by the ALMA maps is typically about 60–70% of the total flux |

## Qualitative findings

- The outflow is mainly gas leaving the disk; tentative slow rotation seen in the outflow lobes  
  > "We think that the rotation of the outflow is tentatively detected in our maps." (6 Origin of the outflowing gas)
- A strong density increase inside 60 AU is not supported by C17O  
  > "Our observations thus do not support a much higher density in the central regions." (5.1 Fitting of CO line maps)

## Claim tuples

- H: Is HCN abundant throughout the Red Rectangle disk? | E: Model H13CN J=4-3 maps with the CO-derived structure and varying abundance | R: Only an H13CN abundance of ~1e-9 within 60 AU reproduces the broad line | F: HCN is abundant only in the inner Keplerian disk, likely formed in a dense PDR | **supported**
- H: Does the nebula contain a rotating disk plus an outflow with specific masses? | E: Nonlocal 2D model fit of ALMA maps and single-dish CO profiles | R: Disk mass ~1.3e-2 Msun, outflow ~1.2e-3 Msun | F: The disk is about ten times more massive than the CO-rich outflow | **supported**
- H: How long does the disk survive? | E: Compare disk mass with mass-loss rate to the outflow | R: About 8000-10000 yr | F: Disk lifetime is long enough to persist through the post-AGB phase | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Nonlocal treatment needed because LTE and LVG are not valid for rotating disks and optically thin high-J lines  
  > "A complex, nonlocal treatment of radiative transfer is therefore necessary in our case." (3 Line emission model)
- Alternative: Density increase by 100 or 1000 in the inner 60 AU rejected because it overpredicts C17O emission at high velocities  
  > "such a very dense central region would lead to emission that is too intense at moderate velocities over $\pm$ 5 km s$^{-1}$." (Appendix B)
- How they decided it was enough: _not stated_
- Limitation (authors): Flux lost by interferometric over-resolution, especially in the outflow wings, makes the model overpredict outflow emission  
  > "the brightness distributions of the mapped lines can be somewhat overestimated by our model calculations with respect to the observations" (5 Model fitting)
- Limitation (authors): No mathematical uncertainty analysis; the fit was done by inspection  
  > "a mathematical discussion on the uncertainties in our model fitting is very difficult." (5.4 Uncertainties in the model fitting)
- Caveat (inferred, ours): Fit is by eye with no formal degeneracy exploration
- Caveat (inferred, ours): HCN-in-PDR interpretation rests on one noisy map (S/N~20) and assumes CO physical conditions
- Caveat (inferred, ours): Disk lifetime depends on a vague mass-loss estimate
- Caveat (inferred, ours): Reproduction depends on an unreleased code

## Reproducibility

- Data public (paper): Dataset ADS/JAO.ALMA#2011.0.00223.S cited  
  > "We made use of the ALMA dataset ADS/JAO.ALMA#2011.0.00223.S." (footnote)
- Products in archive: _not stated_
- Missing: Radiative transfer code not available
- Missing: Data reduction details only in the 2013 paper
- Missing: Model fitting done by eye without objective criteria
- Data volume (inferred): ~10-50 GB (Cycle 0 Band 7 and 9 data)
- Score (inferred): 3/5, Public data and a clear model parameter table exist, but the code is custom and the fit is subjective.
- Rediscovery candidate: no, The fit uses an unreleased code and is performed by inspection; reduction is deferred to another paper.

## Links

- Method: Bujarrabal & Alcolea (2013) (Radiative transfer code and single-dish fitting)
- Method: Bujarrabal et al. (2013b) (ALMA observations and reduction)
- Companion: Bujarrabal et al. (2013b) (Earlier ALMA maps of 12CO and 13CO)
- Related: Herschel/HIFI

## Checks

```json
{
 "quotes": 57,
 "quotes_ok": 57,
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
  "facts": 77,
  "stated": 41,
  "rate": 0.532
 },
 "evidence_ok": true
}
```
