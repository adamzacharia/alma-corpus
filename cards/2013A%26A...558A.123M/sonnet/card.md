# Probing the jet base of the blazar PKS 1830-211 from the chromatic variability of its lensed images. Serendipitous ALMA observations of a strong gamma-ray flare

`2013A&A...558A.123M` | Astronomy and Astrophysics 2013 | first author: Martí-Vidal, I. | arXiv: 1309.0638 | DOI: 10.1051/0004-6361/201322131

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars
- Question: Can the chromatic, time-variable flux ratio of the two lensed images of PKS 1830-211 during a gamma-ray flare constrain the jet structure and physics near the jet base (core-shift, plasmon ejection)?  
  > "We show that such observations can help constrain the physics of plasmon ejection in regions very close to (if not at) the base of the collimation region in the jet." (Introduction)
- Target **PKS 1830-211**: coordinates _not stated_; z/distance z = 2.507 ± 0.002 (blazar); lens at z = 0.89  
  > "The blazar is located at a redshift of $z$=2.507$\pm$0.002 ((cite: lid99)) and is lensed by a foreground $z$=0.89 galaxy ((cite: wik96))" (Introduction); distance from (cite: lid99); lens (cite: wik96)  
  > "The blazar is located at a redshift of $z$=2.507$\pm$0.002 ((cite: lid99)) and is lensed by a foreground $z$=0.89 galaxy ((cite: wik96))" (Introduction)

## Data provenance

- ALMA projects: 2011.0.00405.S
- bands: B3 (~100 GHz), B6 (250 GHz), B7 (290 and 300 GHz)  
  > "The observations were taken in spectral mode at frequencies around 100 GHz (B3), 250 GHz (B6), 290 GHz (B7), and 300 GHz (B7)" (Observations and data reduction)
- frequencies and spectral setup: four 1.875 GHz-wide spectral windows per tuning, 3840 channels of 0.488 kHz  
  > "For each tuning, four different 1.875 GHz-wide spectral windows were set, each counting 3840 channels separated by 0.488 kHz." (Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~2'' in B3, ~0.5'' in B6 and B7  
  > "The array configuration resulted in a synthesized beam of $\sim$ $2''$ in B3, and $\sim$ $0.5''$ in B6 and B7." (Observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 9-11 April, 22-23 May, 4 June, 15 June 2012  
  > "Data were taken on 9–11 April (B6 and B7), 22–23 May (B3, B6, and B7), 4 June (B3 and B7), and 15 June 2012 (B3 and B6)" (Observations and data reduction)
- pi or archival as stated: Cycle 0 Early Science project on absorption lines (Muller et al., in prep.); used serendipitously for continuum  
  > "The project was not designed as a monitoring of PKS 1830$-$211 and Early Science observations were done under best effort basis from the ALMA observatory" (Observations and data reduction)
- Other facility **Fermi-LAT**: Public daily gamma-ray light curve (>100 MeV) for 2012  
  > "The Fermi-LAT light curve (for energy above 100 MeV) for year 2012, as retrieved from the Fermi-LAT public archive, is shown in Fig. [3](#FigFermi)." (Results)
- External data: Lens time delay of 27.1±0.6 days (NE leading)  
  > "The most precise measurement of the time delay between the two images is 27.1$\pm$0.6 days" (Introduction) [from (cite: bar11)]
- External data: Jet viewing angle 3 deg  
  > "Based on the model of (cite: nai05), we set a jet viewing angle of $\theta = 3^{\circ}$" (Model of the blazar's jet) [from (cite: nai05)]
- External data: Core size of ~0.5 mas at 43 GHz  
  > "(cite: jin03) were able to slightly resolve the core size of PKS 1830$-$211 at 43 GHz in their VLBA observations, getting diameters of $\sim0.5$ mas" (Effects of micro- and milli-lensing?) [from (cite: jin03)]
- Simulation/model as data: Parametric Marscher (1980) jet model with plasmon over-density, conical and concave variants, fitted to flux ratios  
  > "we can perform numerical modelling of the mm-submm emission from the jet, using the parametric model by (cite: mar80)" (Model of the blazar's jet)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan or Neptune; scale from short baselines, bootstrapped to other sources  
  > "The flux calibration was performed by short observations of Titan or Neptune." (Observations and data reduction)
- flux scale uncertainty: ~5% in B3, ~10% in B6 and B7  
  > "We estimate an absolute flux accuracy of the order of $\sim$5% in B3 and $\sim$10% in B6 and B7." (Observations and data reduction)
- self calibration: Phase self-cal using NE+SW point-source model, one complex gain solution every 30 s; fit repeated afterwards  
  > "to perform phase self-calibration, with one complex gain solution every 30 seconds." (Observations and data reduction)

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
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Details of the ALMA project and absorption-line data  
  > "(Muller et al., in preparation). Here, we shall summarize briefly the points relevant for this paper." (Observations and data reduction) [from Muller et al., in preparation]
- uvmultifit visibility fitting software  
  > "We used an in-house developed software (uvmultifit; Martí-Vidal et al., in preparation)" (Observations and data reduction) [from Martí-Vidal et al., in preparation]
- Jet model implementation  
  > "Following (cite: mar80), a simple model of a radio-loud AGN jet can be divided into three parts." (Simplified jet model) [from (cite: mar80)]

### Not stated but needed to reproduce (our reading)

- Spectral windows and calibrators used for bandpass and phase, and CASA version
- Details of the array configurations and baseline lengths
- Exact line-free channel selection
- uvmultifit availability (in preparation)
- Optimizer and initial values for the jet-model least-squares fit
- Numerical details of the jet model code (grid, integration)

## Analysis recipe

1. **Measure NE flux and NE/SW flux ratio per epoch and spectral window**: Visibility model-fitting of two point sources (NE, SW), fitting f_NE and ratio R, after removing line channels; repeated after phase self-calibration  
  > "The continuum emission of the blazar images was thus modelled as two point sources (NE and SW)." (Observations and data reduction); "we have fitted the values $f_{NE}$, the flux density of the NE image, and $\Re$=$f_{NE}$/$f_{SW}$, their flux-density ratio." (Observations and data reduction)
   - software: uvmultifit, CASA
   - parameter: Line-free channels remaining typically >2000  
  > "the remaining number of line-free channels was always large (typically $>$2000)." (Observations and data reduction)
   - assumption: Pseudo-ring and components C, D negligible at ALMA frequencies  
  > "we checked that their contribution becomes negligible for the ALMA observations." (Observations and data reduction)
   - fitting: Uncertainties from covariance matrix at chi2 minimum, scaled so reduced chi2 = 1  
  > "The parameter uncertainties were derived from their covariance matrix, computed at the $\chi^ 2$ minimum, and scaled so that the reduced $\chi^2$ equals unity." (Observations and data reduction)
   - validation: _not stated_
2. **Test micro/milli-lensing as cause of variability**: Compare Einstein radius with core size and timescales  
  > "we get a typical Einstein radius $\theta_E = 1.7$ $\mu$as." (Effects of micro- and milli-lensing?)
   - assumption: Core size scales as nu^-1 for conical jet, from 0.5 mas at 43 GHz  
  > "In the case of a conical jet, the size of the core emission should scale roughly as $\propto \nu^{-1}$" (Effects of micro- and milli-lensing?)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit plasmon-in-jet model (conical and concave) to flux ratios vs time and frequency**: Simplified Marscher jet model with plasmon over-density; flux ratio computed using 27-day lens delay; least-squares minimization against observed ratios  
  > "A direct comparison between the observed ratios and the model predictions allows us to constrain the defining parameters of the jet model by means of least-squares minimization." (Model of the blazar's jet)
   - parameter: Fixed: theta = 3 deg, delay = 27 days, nu0 = 100 GHz, tau = 1  
  > "Opacity, $\tau_{\nu 0}$, at $\nu_0$ and $R_0$" (Table parameters)
   - assumption: Very narrow jet tube; plasmon keeps width and contrast; B scaled to keep particle/field energy ratio  
  > "we assume that the jet tube (where the plasma is confined) is very narrow, so that $r \ll R$ for all $R$." (Implementation of the model)
   - fitting: Parameter ranges reported with max 20% chi2 increase over minimum; 8 (conical) or 9 (concave) parameters  
  > "report the range of values that match the data with a similar quality (maximum increase in the $\chi^ 2$ of 20% with respect to the minimum value)" (Model of the blazar's jet)
   - validation: Compared model flux ratios and spectrum with data; conical model fails to reproduce spectrum (alpha=0.7)  
  > "the conical-jet model is clearly unable to reproduce the optically-thin spectrum seen in the data ($\alpha$=0.7)" (Fit to a conical jet)
4. **Derive core-shift and flare timing**: Estimate core separation from plasmon travel time between tau=1 surfaces; apply lens magnification  
  > "From our jet models, both conical and concave, we estimate a distance of 0.3–0.5 pc between the cores at 100 GHz and 300 GHz." (Constraints on the jet physics)
   - assumption: Plasmon speed close to c; magnification 3-6  
  > "Since the speed of the plasmon is likely close to the speed of light" (Constraints on the jet physics)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **uvmultifit** : Visibility model-fitting of the two lensed images  
  > "We used an in-house developed software (uvmultifit; Martí-Vidal et al., in preparation), based on the common-astronomy-software-applications (CASA) package" (Observations and data reduction)
- **CASA** : Platform for uvmultifit visibility fitting  
  > "based on the common-astronomy-software-applications (CASA) package" (Observations and data reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Flux ratio range | ~1.2 (April), peak ~1.5 (May 22-23), ~1.3 (June) | ~0.001-0.002 per measurement | dimensionless | 1 | The flux ratio varies from a low value of $\Re \sim 1.2$ at the first data points on April 09–11 to a peak of $\Re \sim 1.5$ on May 22–23 |
| Upper bound on flux increase of NE image at 100 GHz | 5 | not stated | percent | 1 | we can set an upper bound to the flux-density increase of only 5% at 100 GHz (observer-frame) during the flare |
| Core distance between 100 and 300 GHz | 0.3-0.5 | not stated | pc | 4 | we estimate a distance of 0.3–0.5 pc between the cores at 100 GHz and 300 GHz. |
| Apparent (lensed) core-shift 100-300 GHz | 5-8 | not stated | microarcsec | 4 | results in an apparent core-shift of 5–8 $\mu$as between 100 and 300 GHz (for a shift of 0.5 pc) |
| Normalized core-shift Omega | ~0.8 | not stated | mas GHz | 4 | Our model suggests a value of $\Omega$ $\sim$0.8 mas GHz |
| Plasmon injection time (concave) | 19.2-19.5 | range | days after 1st epoch | 3 | Injection time of plasmon, $t_0$ (days after 1st epoch) / $19.2 - 19.5$ |
| Density contrast K (concave) | 200-210 | range | dimensionless | 3 | / Density contrast factor, $K$                            / $200 - 210$      / $110 - 140$      /                / |
| Plasmon width (concave) | 1.7-2.0 | range | mpc | 3 | Width of the over-density region, $\Delta$ / $1.7 - 2.0$ mpc |

## Qualitative findings

- Flux-ratio variations are chromatic and imply intrinsic jet structure (core-shift); micro/milli-lensing is excluded by timescale.  
  > "We rule out the possibility of micro- and milli-lensing, based on the timescale of the variability." (Summary and conclusions)
- Submm and gamma-ray flares are co-spatial near the jet base.  
  > "we suggest that both flares are co-spatial, in agreement with the shock-in-jet model of $\gamma$-ray emission." (Summary and conclusions)

## Claim tuples

- H: Is the flux-ratio variability due to micro/milli-lensing? | E: Compare Einstein radii and drift timescales with the core size and observed variability timescales | R: Core size (70-215 microarcsec) far exceeds micro-lensing Einstein radius (1.7 microarcsec); milli-lensing too slow for days-weeks, intra-day variability unexplained | F: Intrinsic jet variability is required | **supported**
- H: Can a plasmon travelling in the jet explain the time and frequency dependence of the flux ratio? | E: Fit conical and concave jet models with a plasmon using the 27-day lens delay | R: Both reproduce the general trend; concave also reproduces the spectrum; 300 GHz May intra-day ratios need an extra flare | F: Concave jet with a narrow dense plasmon near the jet base is favored | **partially**
- H: Where do the gamma-ray and submm flares originate? | E: Compare model-derived injection time with Fermi-LAT flare | R: Time lag at most a few days | F: Flares co-spatial near jet base, consistent with shock-in-jet | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Flux ratio between lensed images is free of absolute calibration systematics and the lens delay allows detecting weak flares  
  > "relative fluxes among images are free of absolute calibration effects, so very weak flares can be clearly detected" (Comparison with mm/submm flaring activity in other AGN)
- Alternative: Conical jet model rejected as unable to reproduce the steep spectrum; high-energy cutoff scenario also failed  
  > "we conclude that our data are incompatible with the scenario of a conical jet" (Effects of radiative and adiabatic cooling)
- How they decided it was enough: _not stated_
- Limitation (authors): Many parameters with few data points prevent a statistically robust constraint of parameter space  
  > "makes it difficult to constrain the parameter space in a statistically robust way" (Model of the blazar's jet)
- Limitation (authors): Sparse, irregular time sampling  
  > "hence the loose and irregular time sampling" (Observations and data reduction)
- Caveat (inferred, ours): Model is ad hoc with degenerate parameters; ranges are not formal uncertainties
- Caveat (inferred, ours): Lens time delay and viewing angle fixed from literature
- Caveat (inferred, ours): Flux ratio could also be affected by lens-plane propagation effects not modeled
- Caveat (inferred, ours): Only one epoch group per band so chromatic inference relies on few points

## Reproducibility

- Data public (paper): ALMA data from project 2011.0.00405.S acknowledged; Fermi-LAT data public  
  > "Data from the Fermi-LAT public archive were used." (Acknowledgements)
- Products in archive: _not stated_
- Missing: uvmultifit (in preparation) availability
- Missing: Jet model code and fit procedure details
- Missing: Calibrator and CASA details
- Data volume (inferred): tens of GB (Cycle 0, 12 short epochs, 4 spws of 3840 channels)
- Score (inferred): 3/5, Fitting approach and results are clear and data are public, but software and model code details are not given.
- Rediscovery candidate: no, Flux ratios are numeric and data public, but the in-house uvmultifit and jet model implementation are not available.

## Links

- Method: (cite: mar80) (Parametric jet model used)
- Method: (cite: marti08) (Self-calibration reliability with high dynamic range)
- Companion: Muller et al., in preparation (Absorption-line study from the same ALMA project)
- Companion: (cite: mul13) (T_CMB measurement toward the same source)
- Related: Fermi-LAT monitored sources

## Checks

```json
{
 "quotes": 56,
 "quotes_ok": 56,
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
  "facts": 76,
  "stated": 41,
  "rate": 0.539
 },
 "evidence_ok": true
}
```
