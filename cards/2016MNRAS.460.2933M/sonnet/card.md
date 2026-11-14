# Exocometary gas in the HD 181327 debris ring

`2016MNRAS.460.2933M` | Monthly Notices of the Royal Astronomical Society 2016 | first author: Marino, S. | arXiv: 1605.05331 | DOI: 10.1093/mnras/stw1216

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: debris_disks
- Question: Where are the mm dust and CO gas located in the HD 181327 debris ring, and what is the origin and mass of the CO?  
  > "We present the first ALMA observations to study the dust continuum at 220 GHz and the CO gas distribution, constrain the location of planetesimals" (Introduction)
- Target **HD 181327**: coordinates _not stated_; z/distance 51.8±1.7 pc  
  > "member of the $23\pm3$ Myr old $\beta$ Pic moving group (cite: Mamajek2014) and located at a distance of $51.8\pm1.7$ pc (cite: vanLeeuwen2007)" (Introduction); distance from van Leeuwen 2007  
  > "member of the $23\pm3$ Myr old $\beta$ Pic moving group (cite: Mamajek2014) and located at a distance of $51.8\pm1.7$ pc (cite: vanLeeuwen2007)" (Introduction)

## Data provenance

- ALMA projects: 2012.1.00437.S, 2013.1.00523.S
- bands: Band 6 (1.3 mm, 220 GHz)  
  > "HD 181327 was observed by ALMA in band 6 on 10 March 2014" (2 ALMA observations and imaging)
- frequencies and spectral setup: 3 continuum spws (128 channels, 2 GHz each) plus a CO spw of 244 kHz resolution, 937.5 MHz bandwidth, centred at 230.5 GHz  
  > "The fourth spw was configured with a higher spectral resolution of 244 KHz and total bandwidth of 937.5 MHz (3840 channels), centered at 230.5 GHz" (2 ALMA observations and imaging)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 12-365 m (cycle 1, 26 antennas); 15-650 m (cycle 2, 39 antennas)  
  > "The total number of antennas was 39 with a minimum and maximum projected baselines of 15 and 650 m, respectively." (2 ALMA observations and imaging)
- angular resolution: 0.47"x0.36" (Briggs), 0.69"x0.58" (natural)  
  > "synthetic beam of $0.47\ensuremath{''}\times0.36\ensuremath{''}$ and $0.69\ensuremath{''}\times0.58\ensuremath{''}$, corresponding to Briggs and natural weighting respectively" (2.1 Dust continuum)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 34 min (cycle 1) and 129 min (cycle 2)  
  > "The total time on source excluding overheads was 129 min." (2 ALMA observations and imaging)
- observing dates: 10 March 2014; 4 and 12 June 2014  
  > "on the 4 and 12 June, three new observation runs using the same band were carried out" (2 ALMA observations and imaging)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (230.538 GHz)
- Other facility **HST**: Scattered light ring measurements used for comparison  
  > "HST scattered light observations resolved a debris ring of $\mu$m-sized grains with a peak at $\sim90$ AU and 36 AU wide" (Introduction)
- External data: HST scattered-light ring radius 90.5±1.1 AU and asymmetries  
  > "significantly smaller than at optical wavelengths ($r_0=90.5\pm1.1$)" (4.3 Dust size segregation) [from Stark2014]
- External data: Stellar mass 1.36 Msun  
  > "v$_{\max}=1.9$ km s$^{-1}$ for M$_{\star}=1.36$ M$_{\ensuremath{\odot}}$ (cite: Lebreton2012)" (2.2 12CO (2-1)) [from Lebreton2012]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline  
  > "Calibrations were applied using the pipeline provided by ALMA." (2 ALMA observations and imaging)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan (cycle 1); J2056-472 (cycle 2)  
  > "while Titan and J1819-6365 were used as primary flux and phase calibrators, respectively." (2 ALMA observations and imaging)
- flux scale uncertainty: ~10%  
  > "does not take into account the error on the absolute flux calibration ($\sim10\%$)" (2.1 Dust continuum)
- self calibration: _not stated_

### Imaging

- task: uvmem maximum entropy image synthesis, restored with Clean beam; Clean images used as check  
  > "We call the whole algorithm *uvmem* and the resulting images as “MEM models”." (2.1 Dust continuum)
- deconvolver: _not stated_
- weighting robust: Briggs and natural (robust value not given)  
  > "corresponding to *natural* or *Briggs* weighting" (2.1 Dust continuum)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: first-order polynomial fit to line-free visibilities  
  > "we first subtract the continuum emission from the visibilities fitting a polynomial of the first order at the frequencies where no line emission is expected" (2.2 12CO (2-1))
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: cycle 1 and cycle 2 datasets combined  
  > "We combine the two datasets from both projects to achieve the most complete $u-v$ coverage" (2 ALMA observations and imaging)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: 0.022 mJy/beam (Briggs), 0.015 mJy/beam (natural); CO 1.0 mJy/beam per channel  
  > "We observe a noise level of 0.022 mJy beam$^{-1}$ on the Briggs map, while 0.015 mJy beam$^{-1}$ on the natural map" (2.1 Dust continuum)

### Inherited from earlier work

- Non-LTE CO excitation treatment and photodissociation timescale  
  > "(cite: Matra2015) showed that local thermodynamic equilibrium (LTE) does not necessarily apply in the low gas density environments of debris discs." (3.2 12CO (2-1)) [from Matra2015]
- Electron density power-law index -1.1 assumed equal to beta Pic  
  > "where the power law index was assumed equal to the one derived for $\beta$ Pic (cite: Matra2016inprep)" (3.2 12CO (2-1)) [from Matra2016inprep]
- Collisional cascade mass-loss equations  
  > "using equations 15 and 16 from (cite: Wyatt2008)" (4.4 Collisional timescales) [from Wyatt2008]

### Not stated but needed to reproduce (our reading)

- Briggs robust value
- Line-free channels for continuum fit
- uvmem regularization/hyperparameters and pixel size
- uvmem and uvsim code availability
- Priors' bounds for MCMC and number of walkers/steps
- Pipeline CASA version
- Mask/exact kernel for CO spectrum smoothing

## Analysis recipe

1. **Image continuum**: MEM image synthesis with uvmem, bootstrapped Monte Carlo of 200 iterations, restored with Briggs and natural beams  
  > "The presented images are the median of 200 iterations." (2.1 Dust continuum)
   - software: uvmem
   - fitting: _not stated_
   - validation: Compared with Clean images  
  > "we produce Clean images obtaining roughly the same results" (2.1 Dust continuum)
2. **Fit dust ring model in visibilities**: Axisymmetric Gaussian ring, RADMC-3D images, uvsim visibilities, emcee MCMC  
  > "we compare the observations with an axisymmetric debris disc model in the Visibility space." (3.1 Dust continuum)
   - software: RADMC-3D, uvsim, emcee
   - parameter: Free parameters: r0, h, Δr, Mdust, PA, i, RA and Dec offsets; h lower limit 0.03  
  > "The free parameters in our model image and visibilities are $r_0$, $h$, $\Delta r$, $M_{\mathrm{dust}}$, PA, inclination ($i$) and RA- and decl-offset." (3.1 Dust continuum)
   - assumption: Astrosilicate, 3.5 g/cm3, Dohnanyi q=-3.5, amin 1.3 um, amax 1 cm, kappa_abs=1.1 cm2/g at 1.3 mm  
  > "We assume a Dohnanyi-like size distribution with a power law index of -3.5, and minimum and maximum grain size $a_{\min}=1.3 \mu$m and $a_{\max}=1.0$ cm." (3.1 Dust continuum)
   - fitting: emcee affine-invariant sampler, uniform priors, likelihood ∝ exp(-chi2/2)  
  > "The likelihood function is defined proportional to $\exp[-\chi^2/2]$" (3.1 Dust continuum)
   - validation: chi2 differs by 0.2% from MEM model; residuals consistent with noise  
  > "When we compare the $\chi^2$ of our best axisymmetric model with the MEM model we find a difference of 0.2%." (3.1 Dust continuum)
3. **Detect CO and measure flux**: Subtract continuum, integrate in elliptical mask and velocity range maximising S/N  
  > "we compute the total flux inside an elliptic mask and between a frequency or velocity range that we vary" (2.2 12CO (2-1))
   - parameter: Mask 1.4"-2.1" semi-major axis; velocity -2.8 to 2.0 km/s  
  > "minimum and maximum semi-major axes of $1.4\ensuremath{''}$ and $2.1\ensuremath{''}$" (2.2 12CO (2-1))
   - fitting: _not stated_
   - validation: _not stated_
4. **Fit non-LTE CO model for gas mass**: RADMC-3D non-LTE models in image space against natural-weighted dirty map; MCMC on MCO, r0, Δr over grid of Tk and electron density  
  > "The free parameters in the MCMC are the CO gas mass (M$_\mathrm{CO}$), ring radius ($r_0$) and FWHM of the ring ($\Delta r$)." (3.2 12CO (2-1))
   - software: RADMC-3D
   - parameter: ne0 between 1e-2 and 1e7 cm-3; Tk half to twice dust temperature (50 K)  
  > "We vary n$_{\mathrm{e}^{-}}^{0}$between 10$^{-2}$-$10^{7}$ cm$^{-3}$ to cover from the radiation-dominated regime to LTE." (3.2 12CO (2-1))
   - assumption: h=0.07 and orientation fixed to dust fit; Keplerian rotation; systemic velocity 0.1 km/s; electrons as collision partner  
  > "with a fixed vertical aspect ratio $h$ of 0.07 and fixed disc orientation" (3.2 12CO (2-1))
   - fitting: MCMC, likelihood ∝ exp(-chi2/2) accounting for independent beams and channel correlation  
  > "taking into account the number of independent beams in the image and the correlation between adjacent channels in ALMA data" (3.2 12CO (2-1))
   - validation: Model spectrum compared with half-disc spectra  
  > "The model spectrum matches roughly the observed CO line profile." (3.2 12CO (2-1))
5. **Derive collisional mass loss and cometary CO ice fraction**: Steady-state collisional cascade and CO photodissociation balance  
  > "In steady state we expect $f_\mathrm{CO}\times \dot{\mathrm{M}}=\mathrm{M}_\mathrm{CO}\times\tau_\mathrm{co}^{-1}$" (4.7 Cometary composition)
   - assumption: e=I=0.05, Q*D=230 J/kg, age 23 Myr  
  > "planetesimal strengths ($Q_\mathrm{D}^{\star}$) independent of size and equal to 230 J kg$^{-1}$" (4.4 Collisional timescales)
   - fitting: _not stated_
   - validation: Compared to Solar system comets  
  > "which is consistent with the CO+CO$_2$ abundances in Solar system comets" (4.7 Cometary composition)

## Software

- **uvmem** : MEM image synthesis  
  > "We call the whole algorithm *uvmem* and the resulting images as “MEM models”." (2.1 Dust continuum)
- **uvsim** : Model visibilities  
  > "while the corresponding visibilities were derived using our tool *uvsim*" (3.1 Dust continuum)
- **RADMC-3D** 0.39: Synthetic images, non-LTE CO  
  > "Synthetic images are computed using RADMC-3D[^2] (cite: RADMC3D0.39)" (3.1 Dust continuum)
- **emcee** : MCMC sampling  
  > "with the public python module *emcee* that implements the Goodman & Weare’s Affine Invariant MCMC Ensemble sampler" (3.1 Dust continuum)
- **CASA** : Cycle 3 antenna configurations for simulated observations  
  > "Using the antenna configurations for cycle 3 provided in the CASA software, we simulate ALMA observations" (4.9 Scale height)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Dust ring radius r0 | 86.0 | 0.4 | AU | 2 | $r_{0}$ \[AU\] |
| Dust ring FWHM | 23.2 | 1.0 | AU | 2 | a radial width of $23.2\pm1.0$ AU |
| Dust mass in main ring | 0.442 | 0.005 | Mearth | 2 | The derived total dust mass in the main ring is $0.442\pm0.005$ M$_{\oplus}$. |
| Inclination | 30.0 | 0.7 | deg | 2 | $30.0\pm0.7$ |
| Aspect ratio h upper limit | 0.14 | 99.7% confidence | dimensionless | 2 | we can put a 99.7% confidence upper limit of 0.14 for $h$ |
| Continuum flux (natural map) | 7.9 | 0.2 | mJy | 1 | is $7.9\pm0.2$ mJy |
| Integrated CO flux | 30.1 | 5.4 | mJy km/s | 3 | The integrated flux where the S/N is maximised is $30.1\pm 5.4$ mJy km s$^{-1}$ (5.6$\sigma$). |
| CO mass (ne0=100 cm-3, Tgas=Tdust) | 1.8e-6 | 0.6e-6 | Mearth | 4 | We find M$_\mathrm{CO}=1.8\pm0.6 \times10^{-6}$ M$_{\oplus}$ |
| CO ring radius | 81 | +10/-9 | AU | 4 | $r_0=81^{+10}_{-9}$ AU |
| Planetesimal mass-loss rate | ~3 | not stated | Mearth/Myr | 5 | we find $\dot{\mathrm{M}}\sim 3$ M$_{\oplus}$ Myr$^{-1}$ |
| CO+CO2 ice mass fraction | 0.3%-16% | not stated | fraction | 5 | $f_\mathrm{CO+CO_2}$ is probably between 0.3%-16% |

## Qualitative findings

- Gas and dust co-located; CO is of secondary origin  
  > "We found that the CO is co-located with the dust, favouring a secondary origin scenario." (5 Summary)
- Weak extended continuum emission out to ~200 AU  
  > "we detected low-level emission that extends beyond the primary ring" (5 Summary)

## Claim tuples

- H: Is the mm ring smaller than the optical ring due to grain size segregation? | E: Fit ring model to continuum and compare with HST | R: r0=86.0±0.4 AU vs 90.5±1.1 AU | F: Radiation pressure segregation | **supported**
- H: Is the CO primordial or secondary? | E: Non-LTE modelling and photodissociation/shielding estimates | R: Low column densities, co-location with dust | F: Secondary, released from icy planetesimals | **supported**
- H: Does gas shape the dust ring? | E: Estimate stopping times and dust-to-gas ratio | R: Stopping time for mm grains much longer than instability range | F: Gas unlikely to shape the dust | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Giant collision explanation of scattered-light asymmetry rejected as very unlikely  
  > "thus, very unlikely" (4.1 Axisymmetry)
- How they decided it was enough: _not stated_
- Limitation (authors): Dust mass depends strongly on assumed composition and amax; h not fully constrained  
  > "On the other hand the scale height is not fully constrained." (3.1 Dust continuum)
- Caveat (inferred, ours): Custom unreleased tools uvmem/uvsim hinder replication
- Caveat (inferred, ours): CO detection only ~5.6 sigma
- Caveat (inferred, ours): Gas mass depends on assumed collisional partner and temperature
- Caveat (inferred, ours): Extended emission could be a background contaminant

## Reproducibility

- Data public (paper): Archive project codes listed in acknowledgements  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00437.S and ADS/JAO.ALMA#2013.1.00523.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: uvmem/uvsim code
- Missing: MCMC settings
- Missing: Robust value
- Data volume (inferred): ~50-150 GB raw for two projects
- Score (inferred): 3/5, Public data and a clear model description, but custom unreleased codes and missing MCMC and imaging details.
- Rediscovery candidate: no, Key results depend on unreleased uvmem/uvsim tools and unstated settings.

## Links

- Method: Matra2015 (Non-LTE CO modelling in debris discs)
- Companion: Stark2014 (HST scattered light of HD 181327)

## Checks

```json
{
 "quotes": 68,
 "quotes_ok": 68,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 79,
  "stated": 50,
  "rate": 0.633
 },
 "evidence_ok": true
}
```
