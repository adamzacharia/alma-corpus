# Morphology of the <SUP>13</SUP>CO(3-2) millimetre emission across the gas disc surrounding the triple protostar GG Tau A using ALMA observations

`2018RAA....18...31P` | Research in Astronomy and Astrophysics 2018 | first author: Phuong, Nguyen Thi | arXiv: 1801.00861 | DOI: 10.1088/1674-4527/18/3/31

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks
- Question: What are the geometry, thickness, integrated-intensity variations, kinematics and line width of the 13CO(3-2) gas disc around GG Tau A, complementing Tang et al.?  
  > "The present analysis aims at complementing that of Tang et al. ((cite: tang16)) by providing new detailed information on the properties of the gas disc." (Introduction)
- Target **GG Tau A**: coordinates RA=4h 32m 30.3s, DEC=17°31'40" (J2000)  
  > "GG Tau A is a triple stellar system, 1 to 5 million years old, located at 140 pc in a hole of the Taurus-Auriga star forming region." (Introduction); "The origin of coordinates at RA=4h 32m 30.3s and DEC=$17^{\circ}\,31'\,40"$ corresponds to year 2000." (OBSERVATIONS AND DATA REDUCTION); z/distance 140 pc  
  > "GG Tau A is a triple stellar system, 1 to 5 million years old, located at 140 pc in a hole of the Taurus-Auriga star forming region." (Introduction); "The origin of coordinates at RA=4h 32m 30.3s and DEC=$17^{\circ}\,31'\,40"$ corresponds to year 2000." (OBSERVATIONS AND DATA REDUCTION); distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00129.S
- bands: _not stated_
- frequencies and spectral setup: 13CO(3-2) channel smoothed to 0.11 km/s, velocities -2 to 15 km/s  
  > "The spectral resolution (channel) has been smoothed to 0.11 km s$^{-1}$ and the Doppler velocity covers between $-2$ and 15 km s$^{-1}$." (OBSERVATIONS AND DATA REDUCTION)
- continuum bandwidth: ~0.9 mm, 330.655 to 344.426 GHz  
  > "The continuum emission was observed at $\sim$0.9 mm wavelength over frequencies covering from 330.655 to 344.426 GHz." (OBSERVATIONS AND DATA REDUCTION)
- arrays: _not stated_
- configurations: _not stated_
- baselines: 28 antennas, longest baseline 1284.3 m  
  > "The number of antennas was 28, the longest baseline being 1284.3 m." (OBSERVATIONS AND DATA REDUCTION)
- angular resolution: continuum beam 0.39x0.29 arcsec PA 56 deg; 13CO beam 0.37x0.31 arcsec PA 80 deg  
  > "The beam size (FWHM) is $0.37\times0.31$ arcsec$^2$ with a position angle of 80$^\circ$." (OBSERVATIONS AND DATA REDUCTION)
- max recoverable scale: _not stated_
- sensitivity: noise sigma 7.2 mJy/beam (0.56 K) per cube element  
  > "a $\sigma$ of 7.2 mJy beam$^{-1}$ (0.56 K)" (3.2 13CO(3-2) line emission)
- time on source: 1.84 hours  
  > "The time spent on source was 1.84 hours." (OBSERVATIONS AND DATA REDUCTION)
- observing dates: November 18 and 19, 2013 (Cycle 1), three blocks  
  > "on November 18 and 19, 2013 in three blocks" (OBSERVATIONS AND DATA REDUCTION)
- pi or archival as stated: _not stated_
- Line: 13CO J=3-2 (not stated)
- External data: Gaussian means and widths of the radial profile from the western half of the gas disc  
  > "The means and widths of the Gaussians are fixed to the values obtained by Tang et al. ((cite: tang16)) when fitting the western half of the gas disc." (3.2 13CO(3-2) line emission) [from Tang et al. (cite: tang16)]
- External data: Systemic velocity 6.38±0.02 km/s  
  > "a systemic velocity of $6.38\pm0.02$ km s$^{-1}$ as used by Dutrey et al. ((cite: dutrey14))" (OBSERVATIONS AND DATA REDUCTION) [from Dutrey et al. (cite: dutrey14)]
- External data: Proper motion [17, -19] mas/yr  
  > "proper motion of \[17, $-$19\] mas per year taken from SIMBAD" (OBSERVATIONS AND DATA REDUCTION) [from SIMBAD]
- External data: Gas temperature 18 K  
  > "at $T=18$ K (Tang et al. (cite: tang16))" (3.5 Line width) [from Tang et al. (cite: tang16)]

## Processing

### Calibration

- pipeline or manual: Continuum merged and calibrated by ALMA staff; 13CO(3-2) calibrated with CASA and GILDAS  
  > "The three blocks of continuum data have been merged and calibrated by the ALMA staff and the $^{13}$CO(3-2) data have been calibrated using CASA[^1] and GILDAS[^2]." (OBSERVATIONS AND DATA REDUCTION)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: 13CO(3-2) self-calibrated  
  > "The $^{13}$CO(3-2) emission was self-calibrated." (OBSERVATIONS AND DATA REDUCTION)

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
- smoothing: Spectral resolution smoothed to 0.11 km/s  
  > "The spectral resolution (channel) has been smoothed to 0.11 km s$^{-1}$" (OBSERVATIONS AND DATA REDUCTION)
- final beam: 0.37x0.31 arcsec PA 80 deg (line)  
  > "The beam size (FWHM) is $0.37\times0.31$ arcsec$^2$ with a position angle of 80$^\circ$." (OBSERVATIONS AND DATA REDUCTION)
- final rms: _not stated_

### Inherited from earlier work

- Data already presented, with calibration details, in Tang et al.  
  > "that have been presented earlier by Tang et al. ((cite: tang16)) together with $^{12}$CO(3-2) observations" (Introduction) [from Tang et al. (cite: tang16)]
- Systemic velocity as used for 12CO(6-5)  
  > "as used by Dutrey et al. ((cite: dutrey14)) for $^{12}$CO(6-5)" (OBSERVATIONS AND DATA REDUCTION) [from Dutrey et al. (cite: dutrey14)]

### Not stated but needed to reproduce (our reading)

- Imaging parameters (weighting, robust, cell size, deconvolver, masking)
- Self-calibration solution intervals and reference
- Continuum subtraction and line-free channels
- Exact Tang et al. Gaussian parameters used for the radial fit
- Which CASA/GILDAS versions
- Rest frequency adopted

## Analysis recipe

1. **Continuum ring geometry**: Image-plane projections, Gaussian fits, and ellipse fit of weighted mean radius vs position angle  
  > "A fit of the dependence of $<R>$ on $\varphi$ as an ellipse of semi-major and semi-minor axes $a_0$ and $b_0$ and offset by $\Delta x$ and $\Delta y$" (3.1 Continuum data)
   - parameter: ring interval 1<R<2 arcsec; central source excluded with R'>0.5 arcsec  
  > "over the interval $1<R<2$ arcsec" (3.1 Continuum data)
   - assumption: Circular ring tilted about a rotated x axis  
  > "a tilt with respect to the sky plane $\theta=\cos^{-1}(1.38/1.62)=32^{\circ} \pm 4^\circ$ of a circular ring" (3.1 Continuum data)
   - fitting: _not stated_
   - validation: Compared with Tang et al. and Dutrey et al. values  
  > "These results confirm the values quoted by Tang et al. ((cite: tang16))" (3.1 Continuum data)
2. **Gas disc geometry from integrated intensity and mean velocity**: Ellipse fit of weighted mean R and fit <Vz>=V0-DeltaV cos(phi-phi0) in ring 0.54<r<2 arcsec  
  > "a fit of the form $<V_z>=V_0-\Delta V \cos(\varphi-\varphi_0)$ gives $V_0=0.05$ km s$^{-1}$" (3.2 13CO(3-2) line emission)
   - parameter: |Vz|<2 km/s restriction  
  > "we restrict the Doppler velocity range to $|V_z|<2$ km s$^{-1}$ unless specified otherwise" (3.2 13CO(3-2) line emission)
   - fitting: _not stated_
   - validation: Compared with dust fit and Dutrey et al. values  
  > "again in excellent agreement with the value obtained from the dust fit" (3.2 13CO(3-2) line emission)
3. **Disc thickness upper limit from inner edge sharpness**: Gaussian fits to inner-edge rise in four 60 deg sectors in disc plane (r) and sky plane (R); compare major vs minor axis sigma  
  > "we fit a Gaussian to the rise of each distribution, between 0.5 and 1.5 arcsec in $r$." (4.1)
   - parameter: disc coordinates zeta=y/cos(theta), tilt 35 deg, 99x81 pixels of 0.06 arcsec  
  > "we use $99\times81$ pixels of $0.06\times0.06$ arcsec$^2$ on the sky map" (4. DETAILED PROPERTIES OF THE GAS DISC)
   - assumption: Tilt 35 deg; beam, intrinsic smearing and thickness terms add in quadrature  
  > "we assume a tilt $\theta=35^\circ$ of the disc plane" (4. DETAILED PROPERTIES OF THE GAS DISC)
   - fitting: _not stated_
   - validation: Width of sectors changed to 40 deg; interval varied  
  > "We have checked that this result is independent of the width of the angular sectors" (4.1)
4. **Azimuthal variations of integrated intensity**: Map in disc plane of measured integrated intensity minus its azimuthal average at same r  
  > "the map in the disc plane of the difference between the measured integrated intensity and its value averaged over $\omega$ at the same value of $r$" (4.2)
   - fitting: _not stated_
   - validation: _not stated_
5. **Rotation and infall kinematics**: Fit sine and cosine terms of Vz vs omega; compute Vrot=Vz/(sin theta sin omega) with |sin omega|>0.3; power-law fit of Vrot r^1/2  
  > "we can calculate $V_{rot}=V_z(\sin\theta\sin\omega)^{-1}$ for each data-cube element" (4.3)
   - parameter: brightness-weighted averaging over 0.8<r<2.5 arcsec  
  > "averaged (using brightness as weight) over $0.8<r<2.5$ arcsec" (4.3)
   - assumption: V_fall neglected to first order  
  > "To a good approximation, $V_{fall}$ can be neglected" (4.3)
   - fitting: chi2 minimization of sine and cosine terms; 3 deg uncertainty on omega  
  > "Assuming a 3$^\circ$ uncertainty on $\omega$, corresponding to half a beam sigma at a distance of 1.3 arcsec" (Gas kinematics)
   - validation: 3-sigma cut on cube elements; origin shifted by ±1 pixel  
  > "we compare this result with what is obtained when requiring a 3-$\sigma$ cut on each data-cube element" (4.3)
6. **Line width analysis**: Gaussian fit to dVz distribution; compare with budget of Keplerian shear, instrumental, thermal and opacity broadening; study sigma_vz in r-omega bins and its correlation with integrated intensity  
  > "A Gaussian fit gives a $\sigma$-value of 0.23 km s$^{-1}$." (4.4 Line width)
   - parameter: three r intervals 0.4 arcsec wide between 1.3 and 2.5 arcsec; 24 omega intervals of 15 deg  
  > "three $r$ intervals, 0.4 arcsec wide, covering between 1.3 and 2.5 arcsec and 24 $\omega$-intervals, $15^\circ$ wide" (4.4 Line width)
   - assumption: T=18 K, tau~10 (T,tau)=(36 K,10) at r~1.5 arcsec  
  > "at $T=18$ K (Tang et al. (cite: tang16))" (4.4 Line width)
   - fitting: Linear fit of Delta sigma vs Delta f  
  > "A clear positive correlation is evidenced from the best linear fit, $\Delta\sigma=0.32\,\Delta f$." (Line width)
   - validation: 3-sigma cut gives 0.20 vs 0.23 km/s; noise negligible  
  > "we obtain 0.20 instead of 0.23 km s$^{-1}$" (4.4 Line width)

## Software

- **CASA** : calibration of 13CO(3-2) data  
  > "calibrated using CASA[^1] and GILDAS[^2]" (OBSERVATIONS AND DATA REDUCTION)
- **GILDAS** : calibration of 13CO(3-2) data  
  > "calibrated using CASA[^1] and GILDAS[^2]" (OBSERVATIONS AND DATA REDUCTION)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum ring semi-major axis a0 | 1.62 | not stated | arcsec | 1 | It gives $a_0=1.62$ arcsec and $b_0=1.38$ arcsec |
| Dust ring tilt | 32 | ±4 | deg | 1 | $\theta=\cos^{-1}(1.38/1.62)=32^{\circ} \pm 4^\circ$ |
| Deconvolved dust ring FWHM | 0.528 | 0.035 | arcsec | 1 | gives a de-convolved FWHM of $0.528\pm0.035$ arcsec |
| Gas ellipse a0, b0 | 1.45, 1.19 | not stated | arcsec | 2 | $a_0=1.45$ arcsec and $b_0=1.19$ arcsec |
| Gas disc tilt | 35 | not stated | deg | 2 | The tilt angle is now 35$^\circ$, compared with 32$^\circ$ for the dust. |
| Upper limit on disc thickness sigma_1 (95% CL) | 0.14 | not stated | arcsec | 3 | upper limit for $\sigma_1$ of $\sqrt{(0.29+2\times0.02)^2-0.30^2}=0.14$ arcsec |
| Scale height upper limit at r~1 arcsec | 0.24 (34 au) | 95% CL | arcsec | 3 | scale height $H(r)\sim0.14/\sin35^\circ=0.24$ arcsec (34 au) |
| Upper limit V_fall/V_rot | 9 | 99% CL | percent | 5 | we obtain a 3-$\sigma$ upper limit (99% confidence level) of 9% on the ratio $V_{fall}/V_{rot}$ |
| Rotation power index (|sin omega|>0.707) | -0.51 | not stated | dimensionless | 5 | with a power index of $-0.51$ instead of $-0.63$ |
| Rotation velocity at r=1 arcsec | 3.1 | not stated | km/s | 5 | the rotation velocity at $r=1$ arcsec increasing from 3.0 to 3.1 km s$^{-1}$ |
| Line width sigma_vz | 0.23 | 0.03 | km/s | 6 | compared with $0.23\pm0.03$ km s$^{-1}$ measured |
| Slope of Delta sigma vs Delta f | 0.32 | not stated | dimensionless | 6 | $\Delta\sigma=0.32\,\Delta f$ |
| Azimuthal rms variation of gas integrated intensity | 17 | not stated | percent | 4 | fluctuates around it with an rms of 17% |

## Qualitative findings

- Gas ring is broader than dust ring and peaks at ~87% of its radius  
  > "The gas ring is broader than the dust ring and peaks at smaller distance (typically 87%) to the central stars." (Summary)
- Hot spot confirmed and a northern depression revealed  
  > "found to confirm the presence of a hot spot in the south-eastern quadrant" (Summary)

## Claim tuples

- H: Is the gas disc kinematics dominated by Keplerian rotation with little infall? | E: Sine/cosine fits to Vz vs azimuth and power-law fit of Vrot | R: V_fall/V_rot <9% (99% CL); power index -0.51 | F: Rotation is Keplerian and dominates | **supported**
- H: Is the gas disc vertically thick? | E: Compare inner-edge smearing along major and minor axes | R: scale height upper limit 0.24 arcsec (34 au) at 140 au | F: Consistent with hydrostatic equilibrium at 30 K | **supported**
- H: Line width and its azimuthal/radial variation indicate temperature gradient | E: Line width budget and sigma_vz in r-omega bins | R: sigma_vz rises from ~0.18 to ~0.26 km/s from 2.3 to 1.5 arcsec | F: Possible increase of temperature and opacity inward; turbulence small | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): _not stated_
- Limitation (authors): Planet or companion interpretation requires detailed modelling beyond scope  
  > "would require detailed modelling to be validated" (Summary)
- Caveat (inferred, ours): Image-plane analysis with no forward modelling of the beam or binary
- Caveat (inferred, ours): Uncertainties are mostly estimated by hand, not statistically
- Caveat (inferred, ours): Thin-disc assumption and fixed 35 deg tilt influence results
- Caveat (inferred, ours): Temperature and opacity explanation is qualitative

## Reproducibility

- Data public (paper): Data from ALMA project 2012.1.00129.S, acknowledged as ALMA data  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00129.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Imaging and self-calibration parameters
- Missing: Fitting details and error estimation
- Missing: Exact Tang et al. Gaussian values
- Data volume (inferred): ~20-50 GB for the raw data of three execution blocks
- Score (inferred): 3/5, Data are public and analysis is simple geometric, but imaging details and processing are not given and errors are loosely estimated.
- Rediscovery candidate: no, Calibration/imaging recipe is incomplete and the analysis is custom and image-plane, depending on undisclosed code.

## Links

- Companion: Tang et al. 2016, ApJ 820, 19 (cite: tang16) (Original presentation of the same 13CO(3-2) and 12CO(3-2) ALMA data)
- Companion: Dutrey et al. 2014, Nature 514, 600 (cite: dutrey14) (12CO(6-5) ALMA observations of GG Tau A used for comparison)

## Checks

```json
{
 "quotes": 69,
 "quotes_ok": 69,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 13,
 "numeric_problems": 0,
 "fill": {
  "facts": 82,
  "stated": 48,
  "rate": 0.585
 },
 "evidence_ok": true
}
```
