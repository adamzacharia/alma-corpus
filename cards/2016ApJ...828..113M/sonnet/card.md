# ALMA Observations of the Debris Disk of Solar Analog τ Ceti

`2016ApJ...828..113M` | The Astrophysical Journal 2016 | first author: MacGregor, Meredith A. | arXiv: 1607.02513 | DOI: 10.3847/0004-637X/828/2/113

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: debris_disks, exoplanets
- Question: Where is the inner edge and how wide is the tau Ceti debris belt at 1.3 mm, what does that imply for the proposed five-planet system, and what is the origin of the unresolved central source?  
  > "These new ALMA observations provide limits on the disk location and width, which bear on the proposed planetary system within the disk." (Introduction)
- Target **tau Ceti**: coordinates 01h44m02.299s, -15d56m02.154s (J2000, Dec 2014 phase center)  
  > "The phase center for the December SB was $\alpha = 01^\text{h}44^\text{m}02.299$, $\delta = -15\ensuremath{^\circ}56\ensuremath{'}02.154\ensuremath{''}$ (J2000, ICRS reference frame)." (Observations); "is the second closest (cite: vanL07) Solar-type star" (Introduction); z/distance not stated (1'' = 4 AU implies ~3.7 pc)  
  > "probe angular scales of $\sim1\ensuremath{''}$ (4 AU)" (abstract); "is the second closest (cite: vanL07) Solar-type star" (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00588.S
- bands: Band 6 (1.3 mm)  
  > "The $\tau$ Ceti system was observed using Band 6 (1.3 mm) in December 2014 with the ALMA 12-m array." (2 Observations)
- frequencies and spectral setup: Four 2 GHz basebands centered at 226, 228, 242, 244 GHz, 256 channels each, two polarizations  
  > "the correlator was configured to process two polarizations in four 2 GHz-wide basebands centered at 226, 228, 242, and 244 GHz, each with 256 spectral channels." (2 Observations)
- continuum bandwidth: _not stated_
- arrays: ALMA 12-m array (34 antennas) plus ACA (11 antennas)  
  > "For these ACA SBs, 11 operational antennas were available." (2 Observations)
- configurations: _not stated_
- baselines: 12-m: 15-350 m; ACA: 9-50 m  
  > "| 2014 Dec 15 | 12-m  |    34    |   $15-350$    |     41.4     |" (Table 1)
- angular resolution: ~1'' (4 AU) longest baselines  
  > "with the longest baselines sampling to $1\ensuremath{''}$ ($4$ AU) resolution." (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: Natural-weight rms 30 uJy (12-m), 180 uJy (ACA)  
  > "The natural weight rms noise is 30 $\mu$Jy and 180 $\mu$Jy for the 12-m and ACA observations, respectively." (3.1 Continuum Emission)
- time on source: ACA 5.8 and 33.9 min; 12-m 41.4 min  
  > "| 2014 Jul 16 | ACA  |    11    |    $9-50$     |     33.9     |" (Table 1)
- observing dates: 2014 Jul 7, 2014 Jul 16 (ACA); 2014 Dec 15 (12-m)  
  > "| 2014 Jul 7  |  ACA  |    11    |    $9-50$     |     5.8      |" (Table 1)
- pi or archival as stated: _not stated_
- Other facility **Herschel**: Resolved far-IR disk model (inner edge, inclination, PA) from Lawler et al.  
  > "Models of the *Herschel* images derive an inclination of $i = 35\ensuremath{^\circ}\pm10\ensuremath{^\circ}$" (3.2 Emission Modeling Procedure)
- Other facility **JCMT/SCUBA and SCUBA-2**: 850 um total flux used for outer radius limit and belt flux prior  
  > "we take their derived disk radius of 55 AU as an upper limit on $R_\text{out}$" (3.2 Emission Modeling Procedure)
- Other facility **VLA**: 8.7 mm and 2.0 cm stellar flux measurements from Villadsen et al.  
  > "At 8.7 mm, the measured flux density is $25.3\pm3.9$ $\mu$Jy" (4.2 Central Component)
- External data: Inclination 35±10 deg and PA 105±10 deg from Herschel models, assumed for belt  
  > "we assume that the millimeter belt emission is described by the same geometry." (3.2 Emission Modeling Procedure) [from (cite: law14)]
- External data: 850 um flux 5.8±0.6 mJy and 55 AU radius from SCUBA  
  > "obtain a total flux density at 850 $\mu$m for the disk of $5.8\pm0.6$ mJy" (3.2 Emission Modeling Procedure) [from (cite: gre04)]
- External data: Debris disk spectral index 2.58 used to extrapolate 850 um flux to 1.3 mm (1.2±0.2 mJy)  
  > "using the typical spectral index of 2.58 for debris disks at (sub)millimeter wavelengths (cite: gas12)" (3.2 Emission Modeling Procedure) [from (cite: gas12)]
- External data: VLA 8.7 mm flux 25.3±3.9 uJy and 2 cm upper limit  
  > "At 8.7 mm, the measured flux density is $25.3\pm3.9$ $\mu$Jy" (4.2 Central Component) [from (cite: vill14)]
- External data: Stellar radius 0.793±0.004 Rsun  
  > "adopt a value of $0.793\pm0.004$ $R_\odot$" (4.2 Central Component) [from (cite: dif07)]
- Simulation/model as data: PHOENIX stellar atmosphere model extrapolation predicts 0.60 mJy photosphere at 1.3 mm  
  > "an extrapolation of a PHOENIX stellar atmosphere model (cite: hus13) predicts a 1.3 mm flux density of 0.60 mJy" (4.2 Central Component)

## Processing

### Calibration

- pipeline or manual: Each SB calibrated separately in CASA  
  > "The data from all three SBs were calibrated separately using the `CASA` software package (version 4.2.2)." (2 Observations)
- casa version: CASA 4.2.2  
  > "using the `CASA` software package (version 4.2.2)" (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Neptune  
  > "The absolute flux calibration scale was derived from observations of Neptune" (2 Observations)
- flux scale uncertainty: ~10%  
  > "with a systematic uncertainty of $\sim10\%$ (cite: but12)" (2 Observations)
- self calibration: _not stated_

### Imaging

- task: CLEAN, natural weighting, multi-frequency synthesis  
  > "we Fourier inverted the calibrated visibilities with natural weighting and a multi-frequency synthesis with the `CLEAN` algorithm." (2 Observations)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: Gaussian taper, 6'' FWHM, for disk image  
  > "(on-sky FWHM $= 6\ensuremath{''}$)" (2 Observations)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Point source model subtracted with uvsub to isolate disk  
  > "We isolate the disk emission by subtracting a point source model from these data using the CASA task `uvsub`" (2 Observations)
- line free channels: _not stated_
- primary beam correction: Not applied to images; primary beam included in modeling  
  > "thus do not apply a primary beam correction to any of these images." (2 Observations)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: Star image 1.9''x1.0'' PA -87 deg; disk image 6.5''x6.1'' PA 55 deg  
  > "has a synthesized beam size of $6.5\ensuremath{''}\times6.1\ensuremath{''}$ ($24\times22$ AU), and position angle $= 55\ensuremath{^\circ}$." (3.1 Continuum Emission)
- final rms: 30 uJy (12-m), 35 uJy (star-only image, >40 klambda)  
  > "the natural weight rms is higher, 35 $\mu$Jy, since we exclude some baselines." (3.1 Continuum Emission)

### Inherited from earlier work

- Parametric visibility modeling scheme with MCMC  
  > "We make use of the modeling scheme described in (cite: mac13; mac15b)." (3.2 Emission Modeling Procedure) [from (cite: mac13; mac15b)]
- Belt geometry (i, PA) taken from Herschel modeling  
  > "we assume that the millimeter belt emission is described by the same geometry." (3.2 Emission Modeling Procedure) [from (cite: law14)]

### Not stated but needed to reproduce (our reading)

- Number of emcee walkers, steps, burn-in and convergence criteria
- Exact Gaussian prior form (mean, sigma) on F_belt
- Cell size, image size, clean threshold and masks
- Flux calibrator/phase calibrator details beyond names; bandpass calibrator naming
- Whether visibilities were averaged or channel-weighted before fitting
- Holland et al. SCUBA-2 flux is in prep, unavailable
- Stellar distance adopted for AU conversion

## Analysis recipe

1. **Image continuum and separate star from disk**: CLEAN with natural weights and 6'' taper; uvsub point-source subtraction for disk; baselines >40 klambda untapered for star  
  > "To isolate the stellar component, we image with `CLEAN` and no taper, only including baselines longer than 40 k$\lambda$" (2 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: Star position compared with expected position within 0.14'' uncertainty  
  > "The position of the observed central source is coincident with the expected stellar position within this uncertainty." (3.1 Continuum Emission)
2. **Fit parametric belt plus point source to 12-m visibilities**: Thin axisymmetric belt with power-law surface density, model visibilities via python uvmodel implementation, multiplied by Gaussian primary beam, MCMC fit  
  > "we construct parametric models of the 1.3 mm disk emission and then compute corresponding model visibilities using a python implementation of the Miriad `uvmodel` task" (3.2 Emission Modeling Procedure)
   - software: emcee, vis_sample
   - parameter: Free: Rin, Rout, Fbelt, Fcen, gamma; Rout <= 55 AU; gamma in -4 to 4; uniform priors  
  > "For all parameters, we assume uniform priors and require that the model be physically plausible: $F_\text{cen} \geq 0$, and $0 \leq R_\text{in} < R_\text{out} \leq 55$ AU." (3.2 Emission Modeling Procedure)
   - parameter: Gaussian prior 0.6 mJy <= Fbelt <= 1.6 mJy  
  > "allows us to constrain the total flux density of our models with a Gaussian prior, $0.6\text{ mJy}\leq F_\text{belt}\leq1.6\text{ mJy}$" (Emission Modeling Procedure)
   - assumption: T ∝ r^-0.5 blackbody; i=35 deg, PA=105 deg from Herschel; no offsets fitted  
  > "temperature is assumed to follow a power law, $T\propto r^{-0.5}$, approximating radiative equilibrium for blackbody grains." (3.2 Emission Modeling Procedure)
   - fitting: emcee affine-invariant ensemble MCMC, uniform priors  
  > "This affine-invariant ensemble sampler for MCMC, enables us to accurately sample the posterior probability functions of all model parameters" (3.2 Emission Modeling Procedure)
   - validation: Reduced chi2 1.1; residual image shows no significant features; deprojected visibilities compared with model  
  > "yields a final best-fit model with a reduced $\chi^2$ value of 1.1." (3.3 Results of Model Fits)
3. **Derive belt width and stellar brightness temperature and spectral index**: Fractional width from Rin and Rout; Planck brightness temperature at 1.3 mm, 8.7 mm, 2 cm; spectral index between 1.3 and 8.7 mm  
  > "determine the Planck brightness temperature at all three wavelengths (cite: lis13)" (4.2 Central Component)
   - assumption: Photospheric radius at mm/cm equals optical value 0.793 Rsun  
  > "We assume that the photospheric radius is comparable at optical and millimeter/centimeter wavelengths" (4.2 Central Component)
   - fitting: _not stated_
   - validation: Compared with PHOENIX photosphere and mid-IR extrapolation  
  > "an extrapolation of a PHOENIX stellar atmosphere model (cite: hus13) predicts a 1.3 mm flux density of 0.60 mJy (with 5% uncertainty)." (Central Component)

## Software

- **CASA** 4.2.2: Calibration, CLEAN imaging, uvsub  
  > "using the `CASA` software package (version 4.2.2)" (2 Observations)
- **emcee** : MCMC sampling of model parameters  
  > "we employ the `emcee` Markov Chain Monte Carlo (MCMC) package (cite: for13)" (3.2 Emission Modeling Procedure)
- **vis_sample** : Python implementation of Miriad uvmodel for model visibilities (open source)  
  > "The code used to perform this part of the analysis is open source and freely available" (footnote)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Belt inner radius | 6.2 | +9.8/-4.6 | AU | 2 | / $R_\text{in}$ / Belt inner radius (AU) / $6.2$ / $+9.8,-4.6$ / |
| Belt outer radius | 52 | +3/-8 | AU | 2 | / $R_\text{out}$ / Belt outer radius (AU) / $52.$ / $+3.,-8.$ / |
| Belt flux density | 1.0 | +0.6/-0.4 | mJy | 2 | The best-fit total belt flux density is $F_\text{belt} = 1.0^{+0.6}_{-0.4}$ mJy |
| Surface density index gamma | -0.3 | +1.9/-1.3 | dimensionless | 2 | $\gamma=-0.3^{+1.9}_{-1.3}$ |
| Central source flux density at 1.3 mm | 0.69 | +0.02/-0.05 | mJy | 2 | with a flux density of $0.69^{+0.02}_{-0.05}$ mJy |
| Fractional width DeltaR/R | 1.6 | +0.3/-0.6 | dimensionless | 3 | the fractional width of the $\tau$ Ceti disk is $\Delta R/R = 1.6^{+0.3}_{-0.6}$ |
| DeltaR/R lower limit (99%) | > 0.75 | not stated | dimensionless | 3 | At $99\%$ confidence, $\Delta R/R > 0.75$. |
| Rin upper limit (99%) | < 25 | not stated | AU | 3 | we can place a strong upper limit, $R_\text{in}<25$ AU with $99\%$ ($3\sigma$) confidence. |
| Brightness temperature at 1.3 mm | 5,800 | ±200 | K | 3 | At 1.3 mm this analysis yields $T_B = 5,800\pm200$ K |
| Spectral index 1.3-8.7 mm of central source | 1.74 | ±0.15 | dimensionless | 3 | the spectral index of the central peak in our observations of $\tau$ Ceti is $1.74\pm0.15$ |

## Qualitative findings

- Belt is nearly face-on at ~12'' (~44 AU) from the star with patchy emission (~6 sigma); the ACA data do not detect it  
  > "patchy emission ($\sim6\sigma$) from a nearly face-on (low inclination) dust disk" (3.1 Continuum Emission)

## Claim tuples

- H: Is the tau Ceti belt broad rather than a narrow ring? | E: Parametric visibility fit with MCMC to 12-m data | R: DeltaR/R > 0.75 at 99% confidence; Rin < 25 AU | F: Belt is broad, like HD 107146 and unlike Kuiper Belt/Fomalhaut | **supported**
- H: Does the inner edge location constrain the proposed five-planet system? | E: Fit Rin and compare with Herschel and planet orbits | R: Rin = 6.2 +9.8/-4.6 AU, consistent with Herschel | F: Data cannot discriminate; short-baseline sensitivity insufficient | **partially**
- H: What is the origin of the central unresolved source? | E: Compare 1.3 mm flux with photosphere predictions and VLA data; compute brightness temperatures and spectral index | R: 0.69 mJy vs 0.60 mJy predicted; TB 5800 K; spectral index 1.74 | F: Likely a hot stellar chromosphere | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Parametric fitting in the visibility plane, because the disk is only marginally detected in images  
  > "we fit simple parametric models directly to the visibility data within an MCMC framework." (Conclusions)
- Alternative: Ignored the beta-dependence of dust temperature because it is smaller than fit uncertainties  
  > "the expected change in the temperature profile due to $\beta$ is much smaller than the uncertainty in our resulting model fits and we choose to ignore this effect." (3.2 Emission Modeling Procedure)
- How they decided it was enough: _not stated_
- Limitation (authors): No uv coverage below ~20 klambda and low ACA sensitivity prevent tighter constraints on the inner edge  
  > "Note that we are lacking $(u,v)$ coverage on baselines shorter than $\lesssim20$ k$\lambda$, the region of the visibility curve with the most structure." (3.3 Results of Model Fits)
- Caveat (inferred, ours): Fixed inclination and PA from Herschel may bias belt parameters
- Caveat (inferred, ours): Belt flux prior relies on unpublished SCUBA-2 data and extrapolation
- Caveat (inferred, ours): Single-component power-law belt may miss structure
- Caveat (inferred, ours): Marginal belt detection (~6 sigma)

## Reproducibility

- Data public (paper): Project code given in acknowledgments; data from ALMA archive  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00588.S." (Acknowledgments)
- Products in archive: _not stated_
- Code: vis_sample on GitHub (AstroChem/vis_sample)  
  > "The code used to perform this part of the analysis is open source and freely available" (footnote)
- Missing: MCMC settings (walkers, steps, burn-in)
- Missing: Imaging parameters (cell, size, thresholds)
- Missing: Exact Gaussian prior parameters
- Missing: Adopted distance
- Data volume (inferred): ~ few to tens of GB for three SBs
- Score (inferred): 3/5, Public data and open code, clear model, but MCMC and imaging details missing
- Rediscovery candidate: yes, Public data, specified model and priors, numeric results (Rin, Rout, Fcen); some settings must be inferred.

## Links

- Method: (cite: mac13; mac15b) (Visibility modeling scheme)
- Method: (cite: for13) (emcee sampler)
- Companion: (cite: law14) (Herschel disk model)
- Companion: (cite: vill14) (VLA stellar flux measurements)

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
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 74,
  "stated": 52,
  "rate": 0.703
 },
 "evidence_ok": true
}
```
