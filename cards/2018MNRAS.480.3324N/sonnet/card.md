# De-projection of radio observations of axisymmetric expanding circumstellar envelopes

`2018MNRAS.480.3324N` | Monthly Notices of the Royal Astronomical Society 2018 | first author: Nhung, P. T. | arXiv: 1807.10205 | DOI: 10.1093/mnras/sty2005

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: evolved_stars
- Question: How can radio line data cubes of axi-symmetric expanding circumstellar envelopes be de-projected into effective emissivity, and how well can the wind orientation, velocity scale and prolateness be constrained?  
  > "The problem of de-projection of radio line observations of axi-symmetric expanding circumstellar envelopes is studied with the aim of easing their analysis in terms of physics models." (abstract)
- Target **EP Aqr**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **RS Cnc**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.00026.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: EP Aqr beam FWHM 0.78x0.70 arcsec2 (CO 1-0) and 0.33x0.30 arcsec2 (CO 2-1)  
  > "The beam size (FWHM) is respectively $0.78\times0.70$ and $0.33\times0.30$ arcsec$^2$" (4.2 EP Aqr)
- max recoverable scale: _not stated_
- sensitivity: noise 8 and 7 mJy/beam; 0.2 km/s velocity bins  
  > "the noise respectively 8 and 7 mJy beam$^{-1}$ for pixels of respectively $0.2\times 0.2$ and $0.1\times0.1$ arcsec$^2$ and Doppler velocity bins of 0.2 km s$^{-1}$" (4.2 EP Aqr)
- time on source: _not stated_
- observing dates: ALMA Cycle 4  
  > "we use CO(1-0) and CO(2-1) observations made in Cycle 4 of ALMA operation" (4.2 EP Aqr)
- pi or archival as stated: _not stated_
- Line: CO 1-0 (not stated)
- Line: CO 2-1 (not stated)
- Other facility **NOEMA**: CO(2-1) data of RS Cnc  
  > "Here, we use CO(2-1) observations from the upgraded Plateau de Bure interferometer (NOEMA)" (4.1 RS Cnc)
- External data: Earlier wind parameters for RS Cnc (V0, lambda, theta, phi) = (5.0, 0.50, 9 deg, 38 deg)  
  > "gave $(V_0, \lambda, \theta, \varphi)=(5.0\pm0.2$ km s$^{-1}$, 0.50$\pm$0.02, 9$^\circ\pm 6^\circ$, 38$^\circ\pm 2^\circ$)" (4.1 RS Cnc) [from (cite: Nhung2015a)]
- External data: Earlier wind parameters for EP Aqr (6.0 km/s, 0.67, -36 deg, 13 deg)  
  > "($V_0, \lambda, \theta, \varphi$)=(6.0 km s$^{-1}$, 0.67, $-36^\circ$, 13$^\circ$)" (4.2 EP Aqr) [from (cite: Nhung2015b)]
- Simulation/model as data: Simulated data cubes from a simple radial wind model V=V0(1-lambda cos2alpha), V0=5 km/s, emissivity 1/r^2 for 0.5<r<5 arcsec  
  > "in practice, we set it at 5 km s$^{-1}$ for the purpose of illustration." (2 THE FRAMEWORK)

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

- EP Aqr ALMA observations and reduction described elsewhere  
  > "Here, we use CO(1-0) and CO(2-1) observations made in Cycle 4 of ALMA operation (cite: Nhung2018)." (4.2 EP Aqr) [from (cite: Nhung2018)]
- Same uncertainty criterion (10% chi2_rot increase) as for RS Cnc  
  > "Using the same criterion as for RS Cnc to measure the uncertainty on its measurement, namely a 10% increase of $\chi^2_{rot}$" (4.2 EP Aqr) [from Section 4.1 of this paper]

### Not stated but needed to reproduce (our reading)

- ALMA calibration and imaging details for EP Aqr (deferred to Nhung2018)
- Source distances and systemic velocities
- Algorithm for the P/T peak-to-tail ratio
- Definition of the neighbourhood used for rms estimate of Delta f
- Code for de-projection not released

## Analysis recipe

1. **Find position angle theta**: Minimise chi2_rot, the mirror-symmetry mismatch of the data cube about direction theta  
  > "the symmetry plane, and therefore the value of $\theta$, can be simply found by minimizing the quantity" (4 POSITION ANGLE)
   - parameter: Uncertainty taken as 10% increase of chi2_rot above minimum  
  > "we quote as effective uncertainty the value associated with a 10% increase of $\chi^2_{rot}$ with respect to minimum" (4.1 RS Cnc)
   - fitting: _not stated_
   - validation: Tested on simulated cubes with known theta  
  > "shows the dependence of $\chi ^2_{rot}$ on $\theta-\theta_0$ for $\lambda=0.5$ and various values of $\varphi$, with $\theta_0$ being the value of $\theta$ used to produce the simulated effective emissivity." (POSITION ANGLE OF THE PROJECTION OF THE STAR AXIS ON THE SKY PLANE)
2. **Estimate V0 and reject (lambda,phi) with Q and P/T**: Compare per-pixel Vzmin, Vzmax with model values to get V0 per pixel; use rms/mean Q and peak-to-tail ratio P/T to reject configurations  
  > "The ratio $Q=V_{rms}/V_{mean}$ between their rms value $V_{rms}$ and their mean value $V_{mean}$, calculated over the whole image" (5 MAGNITUDE)
   - parameter: Vzmin/Vzmax from brightness above 2 sigma; cuts Q<0.36 and P/T>2 for RS Cnc  
  > "we used brightness in excess of two noise $\sigma$’s and checked that the result was essentially unaffected when using instead one or three noise $\sigma$’s" (4.1 RS Cnc)
   - fitting: _not stated_
   - validation: Checked on simulations and stability against 1 or 3 sigma thresholds  
  > "we used brightness in excess of two noise $\sigma$’s and checked that the result was essentially unaffected when using instead one or three noise $\sigma$’s." (RS Cnc)
3. **Constrain (lambda,phi) with axi-symmetry**: Compute chi2_axi of de-projected effective emissivity about the axis; exclude ambiguous region with harmful extrema; share emissivity equally between two z values  
  > "we simply assign to each of the two associated $z$ values half the de-projected emissivity, thereby avoiding double-counting" (6 MEASURING)
   - parameter: Brightness uncertainty = quadratic sum of noise and 20% of value  
  > "We use as uncertainty on the measured brightness the quadratic sum of 20% of its value and of the noise." (4.2 EP Aqr)
   - assumption: Radial expansion, axi-symmetry, optically thin, no rotation  
  > "Its assumed axi-symmetry is often a good approximation but is only valid for envelopes that are sufficiently optically thin" (7 SUMMARY)
   - fitting: _not stated_
   - validation: Compared with earlier published wind parameters  
  > "This corresponds indeed to values of $Q<0.36$, $P/T>2$ and $\chi^2_{axi}<10$ favoured by the present study." (RS Cnc)

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| EP Aqr theta (CO 1-0) | -20 | ±37 | deg | 1 | gives $\theta= -20^\circ\pm 37^\circ$ and $-31^\circ \pm 43^\circ$ respectively |
| EP Aqr common theta | -25 | ±28 | deg | 1 | consistent with a common value of $-25^\circ\pm 28^\circ$ |
| RS Cnc theta | 7 | ±10 | deg | 1 | namely $\theta$ =7$^\circ\pm$10$^\circ$ |
| EP Aqr mean spectrum width CO(1-0) | 21.30 | not stated | km/s | 2 | $<W_{vz}>=21.30$ km s$^{-1}$ and 21.61 km s$^{-1}$ |

## Qualitative findings

- RS Cnc acceptable region: bipolar, lambda ~0.3-0.8, phi ~15-45 deg  
  > "with $\lambda$ between $\sim$ 0.3 and $\sim$ 0.8 and $\varphi$ between $\sim 15^\circ$ and $\sim 45^\circ$" (4.1 RS Cnc)

## Claim tuples

- H: The de-projection tools can constrain wind orientation and prolateness in real data | E: Applied chi2_rot, Q, P/T and chi2_axi to RS Cnc (NOEMA) and EP Aqr (ALMA) | R: Narrow acceptable region for RS Cnc; broad region for EP Aqr consistent with earlier models | F: Methods select suitable wind configurations but physics modelling is needed to choose among them | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Effective emissivity hides temperature/density; assumes optically thin, radial expansion, axi-symmetry  
  > "The effective emissivity used throughout the paper to describe observations is a convenient quantity that offers simplicity but hides the difficulty of disentangling the effects of temperature from those of density." (7 SUMMARY)
- Caveat (inferred, ours): ALMA data are only an illustration; no reduction details
- Caveat (inferred, ours): No uncertainty propagation or formal fitting
- Caveat (inferred, ours): Lumpy emissivity makes chi2 uncertainties ad hoc

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Reduced EP Aqr cubes
- Missing: Code
- Missing: P/T algorithm
- Data volume (inferred): ~10-50 GB
- Score (inferred): 2/5, Method is analytic, but ALMA data processing and code details are absent.
- Rediscovery candidate: no, Recipe incomplete and results are largely illustrative.

## Links

- Method: (cite: Diep2016) (Earlier general considerations on de-projection and PV diagrams)
- Companion: (cite: Nhung2018) (Source of the EP Aqr ALMA observations)
- Companion: (cite: Homan2018) (Similar ALMA observations of EP Aqr)

## Checks

```json
{
 "quotes": 31,
 "quotes_ok": 31,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 67,
  "stated": 22,
  "rate": 0.328
 },
 "evidence_ok": true
}
```
