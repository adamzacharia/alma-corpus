# Dissecting the disk and the jet of a massive (proto)star: An ALMA view of IRAS 20126+4104

`2025A&A...693A..76C` | Astronomy and Astrophysics 2025 | first author: Cesaroni, R. | arXiv: 2412.06589 | DOI: 10.1051/0004-6361/202452686

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, protoplanetary_disks
- Question: What are the physical and kinematical structure of the disk and jet of the massive (proto)star IRAS 20126+4104?  
  > "The new data allow us to improve on previous similar observations of IRAS 20126+4104 and confirm the existence of a Keplerian accretion disk around a $\sim$12 $M_\odot$ (proto)star." (abstract)
- Target **IRAS 20126+4104**: coordinates RA(ICRS)=20h14m26.0364s, Dec=+41d13m32.516s (phase center)  
  > "The phase center of the observations was $\alpha$(ICRS)=$20^{\rm h}14^{\rm m}26.0364s$ and $\delta$(ICRS)=41$^\circ$13$'$32.516$''$." (Observations and data reduction); "In the following, we adopt a distance of 1.64 kpc because of the smaller error and for consistency with previous studies of IRAS 20126+4104." (Introduction); z/distance 1.64 kpc  
  > "The phase center of the observations was $\alpha$(ICRS)=$20^{\rm h}14^{\rm m}26.0364s$ and $\delta$(ICRS)=41$^\circ$13$'$32.516$''$." (Observations and data reduction); "In the following, we adopt a distance of 1.64 kpc because of the smaller error and for consistency with previous studies of IRAS 20126+4104." (Introduction); distance from H2O maser parallax (Moscadelli et al. 2011)  
  > "The phase center of the observations was $\alpha$(ICRS)=$20^{\rm h}14^{\rm m}26.0364s$ and $\delta$(ICRS)=41$^\circ$13$'$32.516$''$." (Observations and data reduction); "In the following, we adopt a distance of 1.64 kpc because of the smaller error and for consistency with previous studies of IRAS 20126+4104." (Introduction)

## Data provenance

- ALMA projects: 2016.1.00595.S, 2019.1.00199.S
- bands: Band 6 (1.4 mm)  
  > "The ALMA observations of IRAS 20126+4104 were performed in band 6 at three epochs" (Observations and data reduction)
- frequencies and spectral setup: one 1.875 GHz unit and twelve 234 MHz units  
  > "The correlator configuration consisted of one unit of 1.875 GHz and 12 units of 234 MHz." (Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.48"x0.28" (2017 compact only); 0.23"x0.13" (all configurations)  
  > "The synthesized beam of the images is about $0.48\ensuremath{''}\times0.28\ensuremath{''}$ with a position angle (PA) of -7$^\circ$." (Observations and data reduction); "The resulting synthesized beam is approximately $0.23\ensuremath{''}\times0.13\ensuremath{''}$ with a PA of –12$^\circ$." (Observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: May 20, 2017; July 6, 2017; October 25, 2021  
  > "on May 20, 2017, July 6, 2017, and October 25, 2021" (Observations and data reduction)
- pi or archival as stated: _not stated_
- Line: SiO 5-4 (not stated)
- Line: H2CO 3(0,3)-2(0,2), 3(2,2)-2(2,1), 3(2,1)-2(2,0) (not stated)
- Line: CH3CN 12-11 (and 13CH3CN 13-12, CH3(13)CN) (not stated)
- Line: DCN 3-2 (not stated)
- Line: CH3OH 4(-2,3)-3(-1,2) E (not stated)
- External data: Distance 1.64 kpc from H2O maser parallax  
  > "ranges from 1.33$^{+0.19}_{-0.15}$ (Hirota et al. (cite: vera)) to 1.64$\pm$0.05 kpc (Moscadelli et al. (cite: mosca11))" (Introduction) [from Moscadelli et al. (cite: mosca11)]
- External data: Disk PA 53 deg  
  > "The PA of the plane of the disk was estimated to be ${\rm PA_d}$$\simeq$$53\ensuremath{^\circ}$ (Cesaroni et al. (cite: cesa05)) and we assume this value for our analysis." (Evidence for Keplerian rotation) [from Cesaroni et al. (cite: cesa05)]
- External data: Initial jet model parameters phi=9, theta=21, V0/R0=8.3 km/s/arcsec  
  > "As initial guesses for this procedure we used the values obtained by Cesaroni et al. ((cite: cesa99)), namely $\phi$=9$^\circ$, $\theta$=21$^\circ$, and $V_0/R_0$=8.3 km s$^{-1}$ arcsec$^{-1}$." (Appendix: Jet model) [from Cesaroni et al. (cite: cesa99)]

## Processing

### Calibration

- pipeline or manual: ALMA data-reduction pipeline, then manual flagging in CASA  
  > "The data were calibrated with the ALMA data-reduction pipeline and subsequent data flagging and imaging were made with the Common Astronomy Software Applications (CASA) software" (Observations and data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J2148+0657 (2017); J2253+1608 (2021)  
  > "J2025+3343 and J2148+0657 were used as bandpass and flux calibrator, respectively, whereas in 2021, J2253+1608 was used for both calibrations." (Observations and data reduction)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "We created cubes with natural weighting covering all of the correlator units" (Observations and data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: STATCONT for outflow cubes; constant baseline fitted to line-free channels for disk cubes  
  > "we preferred to subtract the continuum from the other cubes by removing a constant baseline fitted to line-free channels selected by visual inspection of the spectra" (Observations and data reduction)
- line free channels: _not stated_
- primary beam correction: applied  
  > "The data were corrected for primary beam attenuation." (Observations and data reduction)
- array combination: outflow cubes: 2017 compact configuration only; disk cubes: 2017+2021 data  
  > "using only the data obtained with the compact configuration in 2017" (Observations and data reduction)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Jet cone model with velocity proportional to distance  
  > "we adopt the model by Cesaroni et al. ((cite: cesa99)), where the bipolar jet is described as a cone where the material is expanding radially with velocity proportional to the distance from the star." (4.1 The jet) [from Cesaroni et al. (cite: cesa99)]
- Disk velocity-field model  
  > "Our model is basically the same as the one used by Sánchez-Monge et al. ((cite: sanch13))" (Appendix: Disk+halo model) [from Sánchez-Monge et al. (cite: sanch13)]
- Accretion rate formula  
  > "This can be estimated from Eq. (4) of Cesaroni et al. ((cite: cesa99))" (5 Discussion) [from Cesaroni et al. (cite: cesa99)]

### Not stated but needed to reproduce (our reading)

- ALMA/CASA version
- line-free channel ranges
- spectral resolution and channel width of cubes
- cell and image size
- rest frequencies and spectroscopy source for lines
- ranges for eta, Trot, Ncol grid search
- H2CO Trot/Ncol conversion details
- parameter ranges for disk model fit
- how many 2017 configurations/baselines

## Analysis recipe

1. **Calibrate and image cubes and continuum**: Pipeline calibration, natural-weighted cubes, STATCONT continuum, GILDAS analysis  
  > "We then obtained a continuum image from the cube spanning the 1.875 GHz bandwidth with STATCONT" (Observations and data reduction)
   - software: CASA, STATCONT, GILDAS
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit jet geometry and kinematics**: Conical radial-expansion model borders compared by eye to SiO map and PV diagrams  
  > "the best fit was obtained using the values derived by Cesaroni et al. ((cite: cesa99)) as initial guesses and then varying these until a good match with the map and PV diagrams was found by eye" (4.1 The jet)
   - parameter: PA_ja fixed at -60 deg; free: theta, phi, V0/R0  
  > "After fixing the PA of the jet axis to ${\rm PA_{ja}}$=–60$^\circ$, the free parameters of the model are the opening angle of the cone, $\theta$" (The jet)
   - fitting: manual by-eye  
  > "varying these until a good match with the map and PV diagrams was found by eye" (4.1 The jet)
   - validation: compared with SiO(2-1) results of Cesaroni et al. 1999  
  > "The only significant difference with respect to the values obtained by Cesaroni et al. ((cite: cesa99)) from lower resolution observations of the SiO(2–1) line" (4.1 The jet)
3. **Jet H2CO Trot and Ncol maps**: Ratio of H2CO 3(0,3)-2(0,2) to averaged 3(2,2)-2(2,1) and 3(2,1)-2(2,0) integrated maps  
  > "we computed the ratio between the map of the ($3_{0,3}$–$2_{0,2}$) line and that obtained by averaging the maps of the ($3_{2,2}$–$2_{2,1}$) and ($3_{2,1}$–$2_{2,0}$) lines" (The jet)
   - parameter: only values with relative errors <60% displayed  
  > "only values with relative errors of $<$60% are displayed" (The jet)
   - assumption: optically thin, LTE  
  > "assuming optically thin emission and local thermodynamic equilibrium (LTE)" (The jet)
   - fitting: _not stated_
   - validation: _not stated_
4. **Disk Trot and Ncol profiles from CH3CN**: Extract TB along hyperbolic branches of DCN PV peaks; least-squares fit of eta*Trot*(1-exp(-tau)) over CH3CN K lines; power-law fits vs radius  
  > "the best fit was obtained by minimizing the expression $\sum_i\left(T_{{\rm B}i}-T_{{\rm B}i}^{\rm mod}\right)^2$" (Derivation of Trot and Ncol)
   - software: GILDAS
   - parameter: lines K=2,3,4,5,7,8 and v8=1 K,l=2,1; at least three lines detected per pixel  
  > "The calculation was done only for the pixels of the PV diagram where at least three lines were detected." (Derivation of Trot and Ncol)
   - assumption: LTE, density >1e7 cm-3  
  > "which can be analyzed under the LTE approximation given the large densities ($>10^7$ cm$^{-3}$" (Derivation of Trot and Ncol)
   - fitting: least squares, free eta, Trot, Ncol  
  > "the best fit was obtained by minimizing the expression $\sum_i\left(T_{{\rm B}i}-T_{{\rm B}i}^{\rm mod}\right)^2$ , where the sum runs over the selected CH$_3$CN lines (see above).
For this purpose, the free variables $\eta$, $T_{\rm rot}$, and $N_{\rm col}$" (4.2.2 Derivation of T_rot and N_col)
   - validation: _not stated_
5. **Disk velocity field fit and envelope opacity**: Minimize sum of squared LSR velocity residuals for CH3CN peaks with Keplerian+infall model; then vary tau0 to reproduce C-shaped peaks  
  > "we minimize the expression $\sum_i\left(V_i^{\rm obs}-V_i^{\rm mod}\right)^2$" (Fit of the LSR velocity)
   - software: CASA
   - parameter: PA_d fixed to 48 deg; Rd=0.3"=490 au  
  > "We fixed ${\rm PA_d}$ to the value obtained from a least-square fit to the peaks of all ground-state $K$ lines" (Fit of the LSR velocity)
   - assumption: kappa_d=0.01 cm2/g; halo density ∝ 1/r; dust-free optically thick thin disk  
  > "where $\kappa_{\rm d}$ is the dust absorption coefficient that we assume to be equal to 0.01 cm$^2$g$^{-1}$" (Fit of the C-shaped pattern)
   - fitting: least squares  
  > "To fit the disk velocity field, we minimize the expression $\sum_i\left(V_i^{\rm obs}-V_i^{\rm mod}\right)^2$" (4.2.4 Fit of the LSR velocity)
   - validation: model peaks qualitatively compared to observed C-shape  
  > "We conclude that the model qualitatively mimics the C-shaped distribution of the data peaks" (Fit of the C-shaped pattern)
6. **Accretion rate, Toomre Q, axis angle**: Analytic formulae using Ncol and Trot profiles  
  > "For $\mbox{$M_{\rm s}$}$=12 $M_\odot$, $R_{\rm d}$=0.3$''$=490 au, $A$=0.42 (see Sect. [4.2.4](#smodd)), and $X_{\rm CH_3CN}$=$10^{-9}$" (Discussion)
   - assumption: X_CH3CN=1e-9, mu=2.8, thermal sigma_v, Tk=Trot  
  > "we further assume $T_{\rm K}$=$\mbox{$T_{\rm rot}$}$" (Discussion)
   - fitting: _not stated_
   - validation: compared with Cesaroni et al. 1999 accretion rate  
  > "a value in reasonable agreement with that obtained by Cesaroni et al. ((cite: cesa99)) from the millimeter continuum emission and the spread in peak velocity among different CH$_3$CN lines" (5 Discussion)

## Software

- **CASA** : flagging, imaging, imfit Gaussian fit of continuum  
  > "We fitted the continuum map with a 2D Gaussian using task *imfit* of CASA." (The disk)
- **STATCONT** : continuum determination and subtraction  
  > "The continuum was subtracted with the STATCONT software" (Observations and data reduction)
- **GILDAS** : analysis of final images  
  > "The final images were converted to GILDAS format and analyzed with the GILDAS" (Observations and data reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Jet opening angle theta | 10 | not stated | deg | 2 | $\phi$=3$^\circ$, $\theta$=10$^\circ$, and $V_0/R_0$=10 km s$^{-1}$ arcsec$^{-1}$ |
| Jet inclination to plane of sky phi | 3 | not stated | deg | 2 | $\phi$=3$^\circ$, $\theta$=10$^\circ$ |
| Jet velocity gradient V0/R0 | 10 | not stated | km/s/arcsec | 2 | $V_0/R_0$=10 km s$^{-1}$ arcsec$^{-1}$=1.3 km s$^{-1}$ pc$^{-1}$ |
| Continuum deconvolved FWHM | 0.71" x 0.58" | 0.04" | arcsec | 1 | The deconvolved full width at half maximum (FWHM) is (0.71$''$$\pm$0.04$''$)$\times$(0.58$''$$\pm$0.04$''$) |
| CH3CN Trot(R) | 1140 R(au)^-0.32 K | not stated | K | 4 | T_{\rm rot}({\rm K}) = 107~\left[\theta({\rm arcsec})\right]^{-0.32} = 1140~\left[R({\rm au})\right]^{-0.32} |
| CH3CN Ncol(R) | 1.7e19 R(au)^-1.3 | not stated | cm-2 | 4 | N_{\rm col}({\rm cm^{-2}}) = 1.1\times10^{15}~\left[\theta({\rm arcsec})\right]^{-1.3} = 1.7\times10^{19}~\left[R({\rm au})\right]^{-1.3} |
| Stellar mass, inclination psi, infall ratio A, Vsys | 12 Msun; 59 deg; 0.42; -4.3 km/s | not stated | mixed | 5 | $V_{\rm sys}$=–4.3 km s$^{-1}$, $\psi$=59$^\circ$, $M_{\rm s}$=12 $M_\odot$, and $A$=0.42 |
| Envelope opacity tau0 and mass | 0.4; 6.7 Msun | not stated | dimensionless; Msun | 5 | was achieved for $\tau_0=0.4$ |
| Accretion rate | 1.7e-3 | not stated | Msun/yr | 6 | we obtain $\dot{M}_{\rm acc}\simeq1.7\times10^{-3}~M_\odot$ yr$^{-1}$ |
| Angle between disk and jet axes | 33 | not stated | deg | 6 | $\arccos(\hat{e}_{\rm j}\cdot\hat{e}_{\rm d})\simeq33\ensuremath{^\circ}$ |

## Qualitative findings

- NW bow shock traced by all molecules; SE only by SiO  
  > "unlike the bow shock to the SE, which is detected only in the SiO line, the one to the NW is traced by all molecules" (The jet)

## Claim tuples

- H: Is the disk Keplerian with additional infall? | E: PV diagrams and disk velocity model fit to CH3CN peaks | R: A=0.42 needed; M=12 Msun | F: Keplerian rotation plus radial velocity ~40% of rotation | **supported**
- H: Is the disk gravitationally stable? | E: Toomre Q from Trot and Ncol profiles | R: Q>1.5 (R/Rd)^-0.36 | F: Disk stable at all radii | **supported**
- H: A dusty envelope explains the C-shaped peak distribution | E: Disk+halo toy model with tau0 varied | R: tau0=0.4 qualitatively reproduces C-shape | F: Envelope absorbs disk surface emission | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: SW asymmetry could be due to a companion or to jet lifting disk material  
  > "we cannot exclude that a mechanism similar to that operating in disk winds is affecting the structure of the circumstellar disk" (Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Disk model is a toy proof of concept; H2CO method unreliable near the star  
  > "The model is intended to be a proof of concept" (A model for the disk)
- Caveat (inferred, ours): By-eye jet fits without uncertainties
- Caveat (inferred, ours): No uncertainties on Trot/Ncol power laws or model parameters
- Caveat (inferred, ours): Assumed CH3CN abundance dominates accretion rate
- Caveat (inferred, ours): Resolved-out flux not quantified

## Reproducibility

- Data public (paper): ALMA project data acknowledged; public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00595.S and ADS/JAO.ALMA#2019.1.00199.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Imaging parameters (cell, size, channel width)
- Missing: line-free channels
- Missing: fit ranges and uncertainties
- Data volume (inferred): ~100-300 GB raw for three epochs
- Score (inferred): 3/5, Data identified and methods described, but many imaging and fitting details are missing and fits are by eye.
- Rediscovery candidate: no, Recipe lacks key imaging details and some fits are by eye.

## Links

- Method: Sánchez-Monge et al. 2018 (cite: statcont) (STATCONT continuum determination)
- Method: Cesaroni et al. 1999 (cite: cesa99) (jet model and accretion rate formula)
- Companion: Cesaroni et al. 2014 (cite: cesa14) (previous disk observations)

## Checks

```json
{
 "quotes": 72,
 "quotes_ok": 72,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2019.1.00199.S"
 ],
 "obscore_codes_not_in_card": [
  "2021.1.00754.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 81,
  "stated": 47,
  "rate": 0.58
 },
 "evidence_ok": true
}
```
