# Shadows cast on the transition disk of HD 135344B. Multiwavelength VLT/SPHERE polarimetric differential imaging

`2016A&A...595A.113S` | Astronomy and Astrophysics 2016 | first author: Stolker, T. | arXiv: 1603.00481 | DOI: 10.1051/0004-6361/201528039

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: protoplanetary_disks
- Question: What are the morphology, shadows, spiral arms and dust properties of the HD 135344B transition disk surface in multiwavelength polarized scattered light, and how do they relate to the inner disk, protoplanets and ALMA sub-mm emission?  
  > "We study the morphology and surface brightness of the disk in scattered light to gain insight into the innermost disk regions, the formation of protoplanets, planet-disk interactions traced in the surface and midplane layers" (abstract)
- Target **HD 135344B (SAO 206462)**: coordinates RA 15h15m48.44s, Dec -37d09m16.059s (J2000)  
  > "Distance \[pc\] | $140 \pm 42$ | \(8\)" (Table 1); "at a distance of $140\pm42$ pc with an estimated age of $8\substack{+8\\-4}$ Myr (cite: vanboekel2005)" (Introduction); z/distance 140 ± 42 pc  
  > "Distance \[pc\] | $140 \pm 42$ | \(8\)" (Table 1); "at a distance of $140\pm42$ pc with an estimated age of $8\substack{+8\\-4}$ Myr (cite: vanboekel2005)" (Introduction); distance from van Boekel et al. 2005  
  > "Distance \[pc\] | $140 \pm 42$ | \(8\)" (Table 1); "at a distance of $140\pm42$ pc with an estimated age of $8\substack{+8\\-4}$ Myr (cite: vanboekel2005)" (Introduction)

## Data provenance

- ALMA projects: 2012.1.00158.S, 2011.0.00724.S
- bands: ALMA Band 9 data from Perez et al. 2014 compared; Band 7 (0.85 mm) continuum used for disk mass  
  > "in order to match the angular resolution of the ALMA band 9 observation from (cite: perez2014)" (5.3 The interplay of surface and midplane); "estimate the disk mass from the optically thin ALMA band 7 (0.85 mm) dust continuum (cite: pinilla2015)" (5.2 On the origin of the spiral arms)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **VLT/SPHERE (ZIMPOL, IRDIS)**: Polarimetric differential imaging in R, I, Y, J bands (main data of the paper)  
  > "obtained polarized scattered light images with ZIMPOL in $R$- and $I$-band and with IRDIS in $Y$- and $J$-band" (abstract)
- External data: ALMA Band 9 continuum image of HD 135344B used for overlay with SPHERE J-band image  
  > "in order to match the angular resolution of the ALMA band 9 observation from (cite: perez2014) (contours in Fig. [13](#fig:sphere_alma))" (5.3 The interplay of surface and midplane) [from (cite: perez2014)]
- External data: Optically thin ALMA band 7 (0.85 mm) dust continuum used for disk mass / Toomre Q  
  > "estimate the disk mass from the optically thin ALMA band 7 (0.85 mm) dust continuum (cite: pinilla2015)" (5.2 On the origin of the spiral arms) [from (cite: pinilla2015)]
- External data: Grain size distribution values for the radiative transfer model from Model 5  
  > "for which we use values from Model 5 of (cite: carmona2014)" (4.1 Radiative transfer) [from (cite: carmona2014)]
- Simulation/model as data: MCMax3D three-zone radiative transfer model of warped/misaligned inner disk producing J-band Q_phi and U_phi images  
  > "we use the 3D radiative transfer code MCMax3D, which fully includes multiple scattering and polarization, to qualitatively reproduce shadow features A, B, and D." (4.1 Radiative transfer)

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

- ZIMPOL/IRDIS PDI data reduction routines (flat, bias, bad pixel, instrumental polarization correction)  
  > "Standard data reduction routines were applied including flat field, bias frame, and bad pixel correction (cite: avenhaus2014b)." (2.1 SPHERE/ZIMPOL) [from (cite: avenhaus2014b)]
- IRDIS J-band photometric calibration approach  
  > "we do a more approximate photometric calibration as described in (cite: quanz2011)" (Photometric calibration) [from (cite: quanz2011)]
- Disk inclination 11 deg and PA 62 deg adopted from literature  
  > "We have assumed a disk inclination of $11\ensuremath{^\circ}$ and a position angle of the major axis of $62\ensuremath{^\circ}$ (see Table [1](#table:main_parameters))" (3.1 Polarized light imagery) [from Table 1 references (10), (11)]

### Not stated but needed to reproduce (our reading)

- ZIMPOL photometric zero points source details (Schmid et al., in prep.) and pipeline code are not public
- Exact MCMax3D settings (photon counts, grid, stellar spectrum, grain opacity files) not given
- Inner/outer disk PSF used for convolution beyond J-band PSF core not detailed
- ALMA data reduction (calibration, imaging, flux, beam) not described; taken from other papers
- Flux/pixel aperture details for S/N and shadow position-angle identification are qualitative
- Pixel-level positions of the spiral-arm maxima points used in the fits

## Analysis recipe

1. **Reduce PDI data to Q_phi and U_phi**: Extract polarization states, flat/bias/dark/bad pixel correction, centering, instrumental polarization correction, convert Q,U to azimuthal Stokes, mean stack  
  > "$Q_\phi$ and $U_\phi$ frames (see Sect. [2.3](#sec:stokes_parameters)) were obtained for each HWP cycle and combined with a mean-stacking." (2.1 SPHERE/ZIMPOL)
   - parameter: HWP offset correction -1.188 deg (ZIMPOL), -1.7 deg (IRDIS)  
  > "We have used a correction of $-1.188\ensuremath{^\circ}$ for the rotational offset of the HWP with respect to true north" (2.1 SPHERE/ZIMPOL)
   - fitting: _not stated_
   - validation: U_phi image used as noise estimate  
  > "the $U_\phi$ image does not contain any scattered light from the disk and can be used to estimate the noise level of the $Q_\phi$ image." (2.3 Azimuthal Stokes parameters)
2. **Measure disk color and surface brightness profiles**: Disk-integrated polarized flux over star flux in annulus 0.1-2.0 arcsec; weighted least squares linear fit; power-law fit of azimuthally averaged profile 0.7-0.9 arcsec in log-log  
  > "We performed a weighted least squares fit of a linear function in log-log space with the weights given by the standard deviations of the $U_\phi$ bins." (3.4 Surface brightness profiles)
   - assumption: Degree of polarization approximately same in R, I, J  
  > "If we assume that the degree of polarization is approximately the same for the three filers" (3.3 Disk color in polarized light)
   - fitting: weighted least squares  
  > "A weighted least squares fit of a linear function shows that the disk scattering efficiency increases towards longer wavelengths." (Disk color in polarized light)
   - validation: _not stated_
3. **Model shadows with radiative transfer**: Three-zone MCMax3D model with misaligned inner disk and warped transition zone; qualitative comparison to J-band radially integrated surface brightness  
  > "The radiative transfer model for HD 135344B consists of three different zones which are independent in their disk structure and dust properties." (4.1 Radiative transfer)
   - software: MCMax3D
   - parameter: p_warp = 0.2; inner disk misalignment 22 deg; zone 1 dust mass 2e-9 Msun; zone 2 dust mass 2e-11 Msun, epsilon=3  
  > "The inner disk requires a $22\ensuremath{^\circ}$ misalignment with the outer disk, a relatively small aspect ratio ($h_0 = 0.01$), and a dust mass of $2\times 10^{-9}$ M$_\odot$" (4.1 Radiative transfer)
   - assumption: 80% silicates and 20% carbon, 25% porosity, DHS void fraction 0.8  
  > "The dust composition is 80% silicates and 20% carbon and the porosity of the grains is approximated with effective medium theory and set to 25%." (4.1 Radiative transfer)
   - fitting: Qualitative manual comparison, not a fit  
  > "we note that the solution is not unique given the large number of free parameters that have an effect on the shadows." (4.1 Radiative transfer)
   - validation: Comparison with removal of zone 2  
  > "The red dashed line shows the surface brightness of the same radiative transfer model but with zone 2 removed." (4.1 Radiative transfer)
4. **Fit spiral arms with planet-induced density wave model**: chi2 minimization on a grid using Rafikov (2002) spiral shape for S1 and S2 maxima, with protoplanets inside or outside the cavity  
  > "The image is deprojected by the disk inclination after which we performed a $\chi^2$ minimization of the parameter grid which consists of 30, 70, and 70 linearly spaced values" (4.2 Spiral arms as tracers of protoplanets)
   - parameter: 27 and 38 points along S1 and S2; h_p in [0.05,0.4]; zeta=3/2; eta=0.25  
  > "by selecting 27 and 38 azimuthally equidistant points of surface brightness maxima along the S1 and S2 spiral arm, respectively." (4.2 Spiral arms as tracers of protoplanets)
   - assumption: Keplerian rotation  
  > "The rotational profile is assumed to be Keplerian with $\zeta=3/2$" (4.2 Spiral arms as tracers of protoplanets)
   - fitting: chi2 grid; probabilities exp(-chi2/2)  
  > "The Bayesian probabilities are determined with $\exp{(-\chi^2/2)}$ from the $\chi^2$ solutions and normalized" (Spiral arm fitting probabilities)
   - validation: _not stated_
5. **Assess gravitational instability and compare with ALMA**: Toomre Q from optically thin ALMA band 7 disk mass; convolve J-band image to ALMA band 9 beam and overlay  
  > "We use the Toomre parameter to estimate the stability of the HD 135344B disk against self-gravity" (5.2 On the origin of the spiral arms)
   - parameter: kappa_nu = 0.1 (nu/1e12 Hz) cm2/g, g/d=100; beam 132x94 mas  
  > "We use $\kappa_\nu = 0.1(\nu/10^{12}{\rm Hz})$ cm$^2$ g$^{-1}$ (cite: beckwith1990)" (5.2 On the origin of the spiral arms)
   - assumption: Keplerian disk, optically thin temperature profile  
  > "We assume a Keplerian disk, optically thin temperature profile" (5.2 On the origin of the spiral arms)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **MCMax3D** : 3D radiative transfer modeling of shadows  
  > "we use the 3D radiative transfer code MCMax3D" (4.1 Radiative transfer)
- **Astropy** : acknowledged as used in research  
  > "This research made use of Astropy, a community-developed core Python package for Astronomy" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Scattered light cavity radius | 0.18 arcsec (25 au) | not stated | arcsec | 2 | has an approximate radius of 0$.\!\!^{\prime\prime}$18 (25 au) |
| Power-law exponents of outer surface brightness (R, I, Y, J) | -4.33, -3.83, -1.22, -2.71 | 0.11, 0.15, 0.40, 0.07 | dimensionless | 2 | The best-fit results of the power law exponents are $-4.33\pm0.11$, $-3.83\pm0.15$, $-1.22\pm0.40$, and $-2.71\pm0.07$ for $R$-, $I$-, $Y$-, and $J$-band |
| Integrated U_phi/Q_phi ratio at maximum S/N | 2.5-3% | not stated | percent | 2 | The integrated $U_\phi$ signal is between 2.5% and 3% of the integrated $Q_\phi$ signal where the S/N is largest |
| SW bright wedge to opposite wedge ratio (r2-scaled) | 3.7 | not stated | dimensionless | 2 | is a factor of 3.7 larger than the mean value from the same sized wedge in opposite direction. |
| Shadow lane position angles A, B, C | -56, 34, 169 | not stated | deg | 2 | we identify three shadow lanes (A, B, and C) at position angles of approximately $-56\ensuremath{^\circ}$, $34\ensuremath{^\circ}$, and $169\ensuremath{^\circ}$, respectively |
| Inner disk misalignment with outer disk | 22 | not stated | deg | 3 | The inner disk requires a $22\ensuremath{^\circ}$ misalignment with the outer disk |
| Best-fit aspect ratio, protoplanets beyond cavity | 0.16 | not stated | dimensionless | 4 | gives a more realistic best-fit result for the aspect ratio, $h_{\rm S1}=0.16$ |
| Cavity edge maximum, J-band | 24.67 | 0.04 | au | 2 | IRDIS $J$-band & $24.67\pm0.04$ & $11.11\pm0.14$ |
| Minimum Toomre Q | ~10 around 80 au | not stated | dimensionless | 5 | with a minimum of $\sim$10 around 80 au |
| West/east integrated brightness ratio 0.7-1.0 arcsec | 1.1 | not stated | dimensionless | 2 | The integrated surface brightness is approximately a factor 1.1 larger on the west side of the disk compared to the east side |

## Qualitative findings

- Disk integrated polarized flux over star flux rises toward longer wavelengths, indicating large aggregate grains in the surface  
  > "We observe an opposite effect which indicates that larger dust grains ($2\pi a\gtrsim\lambda$) dominate the scattering opacity in the disk surface." (3.3 Disk color in polarized light)
- Shadow C appears only in the second epoch (J-band)  
  > "shadow feature C is present in the $J$-band image but appears to be absent in the image projections of epoch 1" (3.5 Shadow features and indications for variability)

## Claim tuples

- H: Are surface brightness depressions shadows cast by a misaligned/warped inner disk? | E: Polar projections of r2-scaled Q_phi and MCMax3D model with three zones | R: Model reproduces shadows A, B, D qualitatively with 22 deg misaligned inner disk and warp | F: Misaligned inner disk and warp can explain A, B and D; C is variable | **partially**
- H: Are the spiral arms driven by protoplanets? | E: Fit of Rafikov spiral shape to S1 and S2 inside or outside cavity | R: Outside-cavity solutions give physical aspect ratio 0.16 but are degenerate | F: Arms best explained by protoplanets exterior to the arms, not uniquely determined; no gap seen to 1 arcsec | **partially**
- H: What grain sizes dominate surface scattering? | E: Disk-to-star polarized flux in R, I, J | R: Positive trend with wavelength | F: Large aggregate grains dominate scattering opacity | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Gravitational instability only marginal (Toomre Q ~10 min)  
  > "which is an order of magnitude above the Toomre criterion when a gas-to-dust ratio of 100 is used" (5.2 On the origin of the spiral arms)
- How they decided it was enough: _not stated_
- Limitation (authors): Radiative transfer solution not unique; no SED or mm fit  
  > "Also, we did not attempt to fit the SED and the resolved millimeter emission." (4.1 Radiative transfer)
- Limitation (authors): IRDIS photometric uncertainty 30-40%  
  > "which leads to an estimated photometric error of 30-40%" (Photometric calibration)
- Caveat (inferred, ours): ALMA used only as comparison from other papers; no independent reduction
- Caveat (inferred, ours): Shadow variability partly confounded by different filters and S/N between epochs
- Caveat (inferred, ours): Spiral fit is chi2 grid with few points; degeneracies
- Caveat (inferred, ours): Shadow model qualitative with no goodness of fit

## Reproducibility

- Data public (paper): ESO program 095.C-0273 SPHERE data; ALMA codes acknowledged  
  > "Based on observations collected at the European Southern Observatory, Chile, ESO No. 095.C-0273(A) and 095.C-0273(D)." (Footnote)
- Products in archive: _not stated_
- Missing: Full MCMax3D input files
- Missing: ZIMPOL zero-point paper (in prep.)
- Missing: ALMA reduction details
- Data volume (inferred): SPHERE data tens of GB; ALMA not reprocessed
- Score (inferred): 3/5, SPHERE processing described but ALMA is minor and model setup incomplete
- Rediscovery candidate: no, ALMA role minor; main data are VLT/SPHERE and recipe partly unpublished.

## Links

- Method: (cite: avenhaus2014b) (PDI data reduction)
- Method: (cite: min2009) (MCMax radiative transfer code)
- Companion: Maire et al., in prep. (SPHERE total intensity images)
- Companion: (cite: perez2014) (ALMA band 9 observations compared)
- Related: ESO 095.C-0273

## Checks

```json
{
 "quotes": 60,
 "quotes_ok": 60,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 81,
  "stated": 39,
  "rate": 0.481
 },
 "evidence_ok": true
}
```
