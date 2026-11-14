# Morphology and kinematics of the gas envelope of Mira Ceti

`2016MNRAS.460..673N` | Monthly Notices of the Royal Astronomical Society 2016 | first author: Nhung, P. T. | arXiv: 1603.00148 | DOI: 10.1093/mnras/stw996

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: evolved_stars
- Question: What are the morphology and kinematics of the 12CO(3-2) gas envelope of the Mira A+B binary, and what is the role of Mira B?  
  > "We have presented a description of the morphology and kinematics of the gas envelope of Mira Ceti using high spatial resolution observations of $^{12}$CO(3-2) emission made by ALMA." (Summary)
- Target **Mira Ceti (Mira A+B)**: coordinates _not stated_; z/distance 100 pc adopted  
  > "In the present work we retain a distance of 100 pc, meaning that an angular distance projected on the sky of 1$''$ corresponds to 100 AU" (Introduction); distance from Hipparcos 107±10 pc; van Leeuwen 2007 91.7 pc; 100 pc retained  
  > "In the present work we retain a distance of 100 pc, meaning that an angular distance projected on the sky of 1$''$ corresponds to 100 AU" (Introduction)

## Data provenance

- ALMA projects: 2013.1.00047.S
- bands: CO(3-2) line  
  > "made on the CO(3-2) line between 12 and 15 June 2014" (Observations and data reduction)
- frequencies and spectral setup: 25-65 km/s in 0.4 km/s channels  
  > "The line Doppler velocity spectrum evaluated from 25 km s$^{-1}$ to 65 km s$^{-1}$ is available in channels of 0.4 km s$^{-1}$." (Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: maximal baseline 650.5 km (as printed)  
  > "configurations including between 34 and 36 antennas and having a maximal baseline of 650.5 km" (Observations and data reduction)
- angular resolution: 0.325'' x 0.309'' FWHM, PA 83.2 deg  
  > "having a beam of angular dimensions of 0.325$''\times$0.309$''$ FWHM at position angle of 83.2$^\circ$" (Observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: ~10.6 minutes  
  > "The total time on source was $\sim$10.6 minutes." (Observations and data reduction)
- observing dates: 12-15 June 2014  
  > "made on the CO(3-2) line between 12 and 15 June 2014" (Observations and data reduction)
- pi or archival as stated: _not stated_
- Line: 12CO J=3-2 (not stated)
- External data: Mira B orbit parameters used to derive space velocity and Doppler shift  
  > "From the parameters of the Mira B orbit derived by (cite: Prieur2002) we evaluate the space velocity of Mira B in the Mira A rest frame to be $\sim$5.0 km s$^{-1}$" (The close environment of the Mira A+B pair) [from (cite: Prieur2002)]

## Processing

### Calibration

- pipeline or manual: Reduced by ALMA staff; archive clean maps used  
  > "The data have been reduced, merged and corrected for the primary beam by the ALMA staff to clean maps" (Observations and data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: yes, ALMA-staff reduced clean maps  
  > "reduced, merged and corrected for the primary beam by the ALMA staff to clean maps using pixel sizes of 0.06$''\times$0.06$''$" (Observations and data reduction)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: 0.06'' x 0.06''  
  > "clean maps using pixel sizes of 0.06$''\times$0.06$''$" (Observations and data reduction)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: applied by ALMA staff  
  > "corrected for the primary beam by the ALMA staff" (Observations and data reduction)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Effective noise varies per velocity channel due to lack of large-scale coverage  
  > "as noted and explained by (cite: Ramstedt2014) using a similar set of observations, the effective noise peaks at different values" (Observations and data reduction) [from (cite: Ramstedt2014)]

### Not stated but needed to reproduce (our reading)

- Exact archive product/MOUS used and its version
- Rest frequency and velocity reference frame
- Exact Mira A and B centroid coordinates for centring
- Details of Gaussian fits for noise shift and width per channel
- Fitting method for Gaussian components and sine wave
- Flux scale uncertainty

## Analysis recipe

1. **Correct effective noise per channel**: Gaussian fit to effective noise peak per velocity channel for 1''<R<7'' to get shift and width; sigma raised ~30% and shift by ~0.04 Jy/arcsec2 for R<1''; cut at 2 sigma  
  > "for each velocity channel separately a shift $-\Delta f(V_x)$ and a width $\sigma_f(V_x)$ from a Gaussian fit to the effective noise peak." (Observations and data reduction)
   - parameter: cut usually at 2 sigma; results checked against 1, 3 sigma and no cut  
  > "We have checked systematically that all results presented here are not significantly affected by a change in the cut level, or even by the absence of cut." (Observations and data reduction)
   - fitting: _not stated_
   - validation: Cut-level robustness check  
  > "We have checked systematically that all results presented here are not significantly affected by a change in the cut level, or even by the absence of cut." (Observations and data reduction)
2. **Moment maps, spectra and P-V diagrams**: Integrate flux over 34-56 km/s, mean velocity maps, velocity spectra in regions, P-V diagrams averaged over the other coordinate  
  > "its integral over the measured Doppler velocity $V_x$, normally between 34 km s$^{-1}$ and 56 km s$^{-1}$, is $F(y,z)=\int{f(y,z,V_x)dV_x}$" (Observations and data reduction)
   - fitting: _not stated_
   - validation: _not stated_
3. **Characterise the bubble as an expanding ring**: By-eye ellipses, elliptic coordinate eta, mean velocity vs eta and azimuth; ring inclination from aspect ratio  
  > "If the ellipse is interpreted as the projection of a circular ring in space, its angle with the plane of the sky is $\sim$50$^\circ$." (The blue-shifted south-eastern bubble)
   - assumption: Circular ring expanding radially at constant velocity; distance 100 pc  
  > "if the ring is expanding radially at constant velocity, as suggested by Fig. [8](#fig8) (right)" (The blue-shifted south-eastern bubble)
   - fitting: _not stated_
   - validation: _not stated_
4. **3-D emissivity maps assuming radial expansion**: x = R Vx/sqrt(Vrad^2-Vx^2); multiply flux by dVx/dx; images in (z, xi) planes at angles omega  
  > "In Fig. [20](#fig20), $V_{rad}$=7 km s$^{-1}$, all Doppler velocities being measured with respect to a mean velocity $V_0$=47.6 km s$^{-1}$." (An overview at larger distances)
   - assumption: Constant radial expansion; visualisation only, underdetermined  
  > "such a model can be constructed for any data cube, whether expanding or not radially, a result of the under-determination of the problem." (An overview at larger distances)
   - fitting: _not stated_
   - validation: Other Vrad and V0 tried, results not strongly different  
  > "Other reasonable choices of $V_{rad}$ and $V_0$ have been tried and the results have been found not to differ strongly from those presented here." (An overview at larger distances)

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Bubble ring expansion velocity | ~1.7 | not stated | km/s | 3 | would be of the order of 1.7 km s$^{-1}$ in space |
| Bubble ring angle with plane of sky | ~50 | not stated | deg | 3 | its angle with the plane of the sky is $\sim$50$^\circ$ |
| Bubble age | ~2000 | not stated | yr | 3 | To span 7.2$''$, meaning $\sim$720 AU, at such velocity takes $\sim$2000 yr. |
| South-western outflow CO(3-2) flux | 7.90 | not stated | Jy km/s | 2 | South-western outflow / 0.5-2.5 / $-$60-120 /  43-52  / 7.90 / |
| Mira A CO(3-2) flux (R<0.5'') | 4.15 | not stated | Jy km/s | 2 | Mira A         /  0-0.5  /   0-360   /  44-52  / 4.15 / |
| Rotation upper limit in central region | ~0.5 | not stated | km/s/arcsec | 2 | the data can accommodate a rotation of $\sim \pm$0.5 km s$^{-1}$ arcsec$^{-1}$ |

## Qualitative findings

- South-western outflow is broad and expands at 5-10 km/s; north-eastern outflow has two blue-shifted arms around a dark region  
  > "the north-eastern outflow consists of two arms, both blue-shifted, bracketing a broad dark region where emission is suppressed." (abstract)

## Claim tuples

- H: Is the gas near Mira B bound to it or flowing from Mira A? | E: Spectra, P-V diagrams and channel maps near Mira A and B, difference spectrum with symmetric position | R: Difference spectrum peaks at 43.6 km/s, 1 km/s lower than 44.5 km/s, and is negative between 45.5 and 50 km/s | F: Gas flows from Mira A toward Mira B (WRLOF-like), with small possible bound contribution | **supported**
- H: Does the blue-shifted bubble trace a slowly expanding ring? | E: Elliptic coordinate analysis of velocity | R: Velocity rises from NE to SW extremity | F: Ring expanding at ~1.7 km/s, inclined ~50 deg, ~2000 yr old | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Lack of large-distance coverage prevents associating red-shifted arcs into spirals  
  > "we are simply unable to unravel them with sufficient confidence from the present data." (Red-shifted arcs)
- Caveat (inferred, ours): Interpretation is qualitative without models or uncertainties
- Caveat (inferred, ours): Distance adopted (100 pc) is rounded
- Caveat (inferred, ours): Ring geometry drawn by eye
- Caveat (inferred, ours): Single epoch and single CO line, so temperature and density are degenerate

## Reproducibility

- Data public (paper): Data public after one year, retrieved via JVO  
  > "The data are retrieved from the JVO portal (http://jvo.nao.ac.jp/portal) operated by the NAOJ." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Noise-fit parameters per channel
- Missing: Precise region definitions beyond approximate values
- Missing: Exact product version
- Data volume (inferred): a few GB
- Score (inferred): 3/5, Public data and simple analysis, but no software named and many by-eye choices.
- Rediscovery candidate: no, Analysis is largely qualitative and by-eye, with few numeric answers.

## Links

- Companion: Ramstedt et al. 2014 (cite: Ramstedt2014) (Earlier ALMA CO(3-2) mapping of Mira)
- Companion: Vlemmings et al. 2015 (cite: Vlemmings2015) (ALMA continuum of Mira A and B)

## Checks

```json
{
 "quotes": 38,
 "quotes_ok": 38,
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
  "facts": 62,
  "stated": 27,
  "rate": 0.435
 },
 "evidence_ok": true
}
```
