# Neutral versus ionized gas kinematics at z ≃ 2.6: the AGN-host starburst galaxy PKS 0529-549

`2018MNRAS.479.5440L` | Monthly Notices of the Royal Astronomical Society 2018 | first author: Lelli, Federico | arXiv: 1807.03321 | DOI: 10.1093/mnras/sty1795

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: Do neutral ([C I]) and ionized ([O III]) gas trace the same kinematics in PKS 0529-549 at z~2.6, and is the [C I] disc dynamically relaxed and baryon-dominated?  
  > "Here we compare neutral and ionized gas kinematics in the starburst galaxy PKS 0529-549 at $z\simeq2.6$" (Introduction)
- Target **PKS 0529-549**: coordinates 05h 30m 25.44s, -54d 54' 23.2" (J2000)  
  > "$z$ (from $V_{\rm sys}$) | $2.570\pm0.001$" (Table 1); "In this cosmology, 1 arcsec = 8.2 kpc at $z= 2.6$." (Introduction); z/distance z = 2.570 ± 0.001  
  > "$z$ (from $V_{\rm sys}$) | $2.570\pm0.001$" (Table 1); "In this cosmology, 1 arcsec = 8.2 kpc at $z= 2.6$." (Introduction); distance from from [C I] systemic velocity  
  > "$z$ (from $V_{\rm sys}$) | $2.570\pm0.001$" (Table 1); "In this cosmology, 1 arcsec = 8.2 kpc at $z= 2.6$." (Introduction)

## Data provenance

- ALMA projects: 2013.1.00521.S
- bands: _not stated_
- frequencies and spectral setup: four 1.875 GHz SPWs at 224.99, 226.87, 239.99, 241.87 GHz  
  > "We used four 1.875 GHz-wide spectral windows centered at 224.99, 226.87, 239.99 and 241.87 GHz." (2.1 ALMA data)
- continuum bandwidth: _not stated_
- arrays: 34 antennas, Cycle 2  
  > "observed on 2 September 2014 during ALMA Cycle 2 with 34 working antennas" (2.1 ALMA data)
- configurations: _not stated_
- baselines: 33 m to 1090 m  
  > "giving maximum and minimum baselines of 1090 m and 33 m, respectively" (2.1 ALMA data)
- angular resolution: 0.43'' x 0.28'', PA 64.5 deg  
  > "The resulting synthesized beam is $0.43'' \times 0.28''$ with a position angle (PA) of 64.5$^{\circ}$." (2.1 ALMA data)
- max recoverable scale: _not stated_
- sensitivity: continuum 0.055 mJy/beam; [C I] 0.55 mJy/beam per 50 km/s channel  
  > "giving a sensitivity of 0.55 mJy beam$^{-1}$ per channel" (2.1 ALMA data)
- time on source: 5 minutes  
  > "The on-source integration time was 5 minutes." (2.1 ALMA data)
- observing dates: 2 September 2014  
  > "PKS 0529-549 was observed on 2 September 2014" (2.1 ALMA data)
- pi or archival as stated: _not stated_
- Line: [C I] 3P2-3P1 (2-1) (809.3435 GHz)
- Other facility **VLT/SINFONI**: [O III] ionized gas IFS cubes  
  > "present IFS data of PKS 0529-549 using SINFONI at the ESO Very Large Telescope (VLT)" (2.2 SINFONI and ATCA data)
- Other facility **ATCA**: 18.5 GHz radio continuum image  
  > "Here we show the uniform-weighted image at 18.5 GHz" (2.2 SINFONI and ATCA data)
- External data: Stellar mass and H-band luminosity from Spitzer SED fit  
  > "For PKS 0529-549, they give $L_{\rm H} \simeq 4 \times 10^{11}$ L$_{\odot}$ and $M_{\star} \simeq 3 \times 10^{11}$ M$_{\odot}$." (3.3 Mass budget) [from (cite: deBreuck2010)]
- External data: WIM mass 2.4e9 Msun  
  > "estimate $2.4\times10^{9}$ M$_{\odot}$ for a fiducial electron density of 500 cm$^{-3}$" (3.3 Mass budget) [from (cite: Nesvadba2017)]
- External data: Local baryonic Tully-Fisher relation from SPARC  
  > "lies on the local baryonic TF relation from the SPARC sample" (4.2 The baryonic Tully-Fisher relation) [from (cite: Lelli2016b; Lelli2016a)]

## Processing

### Calibration

- pipeline or manual: standard CASA pipeline  
  > "The $uv$ data were flagged and calibrated using the standard CASA pipeline." (2.1 ALMA data)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0519-4546 (flux and bandpass)  
  > "The flux and bandpass calibrator was J0519-4546" (2.1 ALMA data)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA clean  
  > "The imaging was performed using the task $clean$ with $Robust=2$" (2.1 ALMA data)
- deconvolver: _not stated_
- weighting robust: Robust=2 (natural)  
  > "$Robust=2$, which corresponds to natural weighting of the visibilities" (2.1 ALMA data)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: interactive Boolean mask, contiguous pixels S/N >~ 2 per channel  
  > "the mask is constructed interactively on a channel-by-channel basis by defining regions in which contiguous pixels have S/N $\gtrsim$ 2" (2.1 ALMA data)
- multiscale scales: _not stated_
- continuum subtraction: image plane, first-order polynomial to line-free channels  
  > "The continuum was subtracted from the [C I] cube in the image plane, after fitting a first-order polynomial to line-free channels." (2.1 ALMA data)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.43'' x 0.28'', PA 64.5 deg  
  > "The resulting synthesized beam is $0.43'' \times 0.28''$" (2.1 ALMA data)
- final rms: 0.055 mJy/beam continuum; 0.55 mJy/beam per channel  
  > "reaching a sensitivity of 0.055 mJy beam$^{-1}$" (2.1 ALMA data)

### Inherited from earlier work

- Global [C I] profile fit and flux  
  > "as estimated from fitting the global [C I] profile (presented in A. Man et al. 2018, in prep.)" (2.1 ALMA data) [from A. Man et al. 2018, in prep.]
- GALMOD procedure  
  > "We use GALMOD following (cite: Lelli2015)" (3.2 Disc modelling) [from (cite: Lelli2015)]
- Pseudo-3sigma contour method  
  > "define a pseudo-3$\sigma$ contour by considering spatial pixels with S/N ratio between 2.75 and 3.25 (cite: Lelli2014c)" (2.1 ALMA data) [from (cite: Lelli2014c)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges for continuum subtraction
- Exact channel mask regions
- 3DBarolo settings (initial estimates, ring geometry, normalization, fit options)
- GALMOD fixed centre, PA, Vsys values and iteration details
- CASA version and clean parameters (cell, image size, threshold)
- Mol mass conversion details (Man et al. in prep.)

## Analysis recipe

1. **Image continuum and [C I] cube**: CASA clean, natural weighting, 50 km/s channels, image-plane continuum subtraction  
  > "The [C I] cube was imaged using a channel width of 50 $\mathrm{km}\,\mathrm{s}^{-1}$" (2.1 ALMA data)
   - software: CASA
   - fitting: _not stated_
   - validation: Tried uv-plane subtraction, found over-subtraction  
  > "sanity checks revealed that the continuum was over-subtracted in this way" (2.1 ALMA data)
2. **Build moment maps**: Boolean-masked moment 0 and intensity-weighted moment 1 in GIPSY  
  > "To build the velocity map (moment one), we estimate an intensity-weighted mean velocity for the pixels inside the Boolean mask." (2.1 ALMA data)
   - software: GIPSY
   - fitting: _not stated_
   - validation: _not stated_
3. **3D disc model of [C I]**: GALMOD trial-and-error for initial estimates and geometry, then 3DBarolo chi2 fit of Vrot and sigma in a single ring  
  > "We use $V_{\rm rot}$ and $\sigma_{\rm V}$ as free parameters, but keep the others fixed to the values estimated with GALMOD." (3.2 Disc modelling)
   - software: GALMOD, 3DBarolo
   - parameter: exponential vertical profile, h = 0.04'' ~ 300 pc  
  > "we assume an exponential vertical profile with fixed $h = 0.04'' \simeq 300$ pc" (3.2 Disc modelling)
   - assumption: parameters constant with radius (single ring)  
  > "we assume that the disc parameters are constant with radius ($R$)" (3.2 Disc modelling)
   - fitting: chi2 minimization; errors by re-running with one variable free  
  > "To estimate errors on each variable, we re-run $^{\rm 3D}$BAROLO leaving such variable free" (3.2 Disc modelling)
   - validation: Compare model with PV diagrams, channel maps, moment map residuals  
  > "we build model cubes and compare them with the observed one using Position-Velocity (PV) diagrams and channel maps" (3.2 Disc modelling)
4. **Mass budget and dynamical mass**: M_R = eps R Vrot^2/G with eps=1; baryonic mass from stellar (literature) + molecular (from [C I] flux) + WIM  
  > "For simplicity, we adopt $\varepsilon = 1$ (spherical geometry)." (3.3 Mass budget)
   - assumption: [C/H2] abundance of M82; factor of 2 uncertainty  
  > "This [C I]$-$to$-$H$_2$ conversion assumes the [C/H$_2$] abundance of the local starburst galaxy M82" (3.3 Mass budget)
   - fitting: _not stated_
   - validation: Compare Mdyn with Mbar at 4 and 8 kpc  
  > "If we extrapolate the measured rotation velocity out to 8 kpc, we get $M_{\rm 8\,kpc} = (1.8\pm0.6) \times 10^{11}$ M$_{\odot}$ which is closer to $M_{\rm bar}$." (Mass budget)
5. **Compare with baryonic Tully-Fisher relation**: Place Vrot and Mbar on local SPARC BTFR  
  > "Figure [4](#fig:BTFR) shows that PKS0529-259 lies on the local baryonic TF relation from the SPARC sample" (4.2 The baryonic Tully-Fisher relation)
   - fitting: _not stated_
   - validation: Discussed Vflat vs intensity-weighted Vrot (20-30%)  
  > "If the rotation curve of PKS 0529-549 has a similar shape, then our intensity-weighted value should not differ from $V_{\rm flat}$ by more than $\sim20-30\%$." (The baryonic Tully-Fisher relation)

## Software

- **CASA** : calibration and imaging  
  > "The data reduction was performed using the Common Astronomy Software Applications (CASA) package" (2.1 ALMA data)
- **GIPSY** : cube analysis, moment maps, GALMOD  
  > "the [C I] cube was analysed using the Groningen Imaging Processing System" (2.1 ALMA data)
- **GALMOD** : 3D disc models by trial and error  
  > "GALMOD needs to be used iteratively by trial and error" (3.2 Disc modelling)
- **3DBarolo** : chi2 fit of Vrot and sigma  
  > "$^{\rm 3D}$BAROLO explores the full parameter space to find a best-fit solution by $\chi^{2}$ minimization" (3.2 Disc modelling)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| [C I](2-1) flux | 2.1 | 0.4 | Jy km/s | 0 | The [C I] flux is $2.1\pm0.4$ Jy $\mathrm{km}\,\mathrm{s}^{-1}$ |
| Vrot | 310 | 50 | km/s | 3 | $V_{\rm rot}$ ($\mathrm{km}\,\mathrm{s}^{-1}$) / $310\pm50$ |
| sigma_V | <~30 | upper limit | km/s | 3 | $\sigma_{\rm V}$ ($\mathrm{km}\,\mathrm{s}^{-1}$) / $\lesssim$30 |
| inclination | 50 | 4 | deg | 3 | $i$ ($^{\circ}$) / $50\pm4$ |
| M_4kpc | 0.9e11 | 0.3e11 | Msun | 4 | thus $M_{\rm 4\, kpc} = (0.9 \pm 0.3) \times10^{11}$ M$_{\odot}$ |
| M_bar | 3.4e11 | 2.0e11 | Msun | 4 | the total baryonic mass of PKS 0529-549 is $M_{\rm bar} = (3.4\pm2.0) \times 10^{11}$ $M_{\odot}$ |
| M_mol | 4e10 | factor of 2 | Msun | 4 | we estimate $M_{\rm mol}\simeq 4 \times 10^{10}$ M$_{\odot}$ |
| [O III] disc fit Vrot/sigma | 0.3 | not stated | dimensionless | 0 | leading to $V_{\rm rot}/\sigma_{\rm V}\simeq0.3$ |

## Qualitative findings

- [C I] and [O III] velocity fields differ in systemic velocity (~300 km/s) and PA (~30 deg); [O III] aligned with radio lobes, likely outflow  
  > "their systemic velocities and position angles differ by $\sim$300 $\mathrm{km}\,\mathrm{s}^{-1}$ and $\sim$30$^{\circ}$, respectively" (abstract)

## Claim tuples

- H: The [C I] velocity gradient traces a rotating disc | E: 3D disc models with GALMOD and 3DBarolo compared with PV diagrams and channel maps | R: Vrot ~310 km/s, sigma <~30 km/s, residuals <2-3 sigma | F: [C I] is a rotating, non-turbulent disc with Vrot/sigma >~ 10 | **supported**
- H: Baryons dominate the inner dynamics | E: Compare dynamical and baryonic masses | R: M_4kpc = 0.9e11, M_8kpc = 1.8e11, M_bar = 3.4e11 Msun | F: Consistent within errors, little dark matter in centre | **partially**
- H: The galaxy follows the local BTFR | E: Plot Vrot and Mbar against SPARC BTFR | R: Lies on the relation | F: Some massive galaxies are relaxed at z~2.6 | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Outflow or merger origin of [C I] gradient disfavoured; merger not definitively ruled out  
  > "The merger origin for the [C I] velocity gradient cannot be definitively ruled out, but we disfavour this scenario" (3.2 Disc modelling)
- How they decided it was enough: _not stated_
- Limitation (authors): Velocity map very uncertain due to beam smearing and low S/N; Sigma not robust  
  > "We stress that the velocity map is very uncertain due to beam smearing effects and the low S/N ratio." (2.1 ALMA data)
- Caveat (inferred, ours): Only ~2 beams across the disc; model parameters depend on initial estimates
- Caveat (inferred, ours): Stellar mass from literature with large uncertainty and unknown SFH
- Caveat (inferred, ours): Single object BTFR conclusion
- Caveat (inferred, ours): Inclination weakly constrained

## Reproducibility

- Data public (paper): ALMA data cited by project code in acknowledgements; SINFONI/ATCA from other papers  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA$\#$2013.1.00521.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: 3DBarolo and GALMOD input parameters
- Missing: Companion papers in prep. for flux and Mmol
- Missing: Mask definition
- Data volume (inferred): ~5-20 GB raw (short 5-min Cycle 2 observation)
- Score (inferred): 3/5, Public ALMA data and clear workflow, but modelling and masking details incomplete and some inputs from in-prep papers.
- Rediscovery candidate: yes, Public data, numeric Vrot/sigma results; recipe moderately complete.

## Links

- Method: (cite: DiTeodoro2015) (3DBarolo)
- Method: (cite: Lelli2015) (GALMOD procedure)
- Companion: A. Man et al. 2018, in prep. ([C I] flux, X-Shooter, Mmol)
- Companion: T. Falkendal et al. 2018, in prep. (continuum SED and SFR)
- Companion: (cite: Nesvadba2017) (SINFONI data)
- Related: SPARC

## Checks

```json
{
 "quotes": 65,
 "quotes_ok": 65,
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
  "stated": 48,
  "rate": 0.632
 },
 "evidence_ok": true
}
```
