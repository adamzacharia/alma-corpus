# The First Bird’s-eye View of a Gravitationally Unstable Accretion Disk in High-mass Star Formation

`2019ApJ...877L..25M` | The Astrophysical Journal Letters 2019 | first author: Motogi, Kazuhito | arXiv: 1905.12983 | DOI: 10.3847/2041-8213/ab212f

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: What is the structure, mass and gravitational stability of the innermost accretion disk and infalling envelope around the nearly face-on high-mass protostar G353.273+0.641?  
  > "This work directly resolved 10$^{2}$-10$^{3}$ au scale and examined these possibilities." (Introduction)
- Target **G353.273+0.641 (G353)**: coordinates 17h26m01.58798s, -34d15m14.9175s (J2000.0)  
  > "G353 is a relatively nearby high-mass object ($\sim$1.7 kpc) without any compact HII region" (Introduction); "The continuum peak position was 17$^{\rm h}$26$^{\rm m}$01$^{\rm s}$.58798, -34$^\circ$15$'$14$''$.9175 (J2000.0)." (Observation and reduction); z/distance ~1.7 kpc  
  > "G353 is a relatively nearby high-mass object ($\sim$1.7 kpc) without any compact HII region" (Introduction); "The continuum peak position was 17$^{\rm h}$26$^{\rm m}$01$^{\rm s}$.58798, -34$^\circ$15$'$14$''$.9175 (J2000.0)." (Observation and reduction); distance from previous studies (Motogi et al. 2016, 2017)  
  > "G353 is a relatively nearby high-mass object ($\sim$1.7 kpc) without any compact HII region" (Introduction); "The continuum peak position was 17$^{\rm h}$26$^{\rm m}$01$^{\rm s}$.58798, -34$^\circ$15$'$14$''$.9175 (J2000.0)." (Observation and reduction)

## Data provenance

- ALMA projects: 2016.1.01068.S
- bands: Band 4, 150 GHz  
  > "centered on 142.692, 144.571, 154.613, and 156.491 GHz (ALMA band 4)" (Observation and reduction)
- frequencies and spectral setup: four 1.875 GHz sub-bands at 142.692, 144.571, 154.613, 156.491 GHz; only 156.491 GHz (488.281 kHz, 0.94 km/s) used for lines  
  > "Only the sub-band at 156.491 GHz, which had the highest spectral resolution of 488.281 kHz (0.94 km s$^{-1}$), was used for the line analysis." (Observation and reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: long baseline, up to ~12 km, 45 antennas  
  > "Forty-five antennas were used in the long baseline configuration (up to $\sim$12 km)." (Observation and reduction)
- baselines: _not stated_
- angular resolution: 0.085x0.050 arcsec continuum; 0.099x0.075 arcsec lines  
  > "Original synthesized beams were 0$''$.085$\times$0$''$.050 (145$\times$85 au$^2$) and 0$''$.099$\times$0$''$.075 (168$\times$128 au$^2$) for the continuum and CH$_{3}$OH lines" (Observation and reduction)
- max recoverable scale: structures larger than 0.5 arcsec resolved out  
  > "any envelope structure larger than 0$\ensuremath{''}$.5 should be resolved out in our data" (Accretion rate and stellar properties)
- sensitivity: _not stated_
- time on source: 5 minutes  
  > "The total on-source time was 5 minutes." (Observation and reduction)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CH3OH J_K 8_0-8_-1 etc. (seven lines) (156.12770-157.24604 GHz (e.g. 156.48886))
- Line: 13CH3OH 8_0-8_-1, 6_0-6_-1, 5_0-5_-1, 4_0-4_-1 (155.69574-156.35640 GHz)
- Other facility **JVLA 45 GHz**: previous 45 GHz continuum compared with new 150 GHz data  
  > "For fair comparison between new 150 GHz data and previous J-VLA 45 GHz data" (Observation and reduction)
- External data: 45 GHz continuum compact component size and flux  
  > "The data at 45 GHz is from (cite: 2017ApJ...849...23M)" (Table 1) [from (cite: 2017ApJ...849...23M)]
- External data: Disk inclination ~8 deg from LOS  
  > "the disk rotational axis is inclined $\sim$ 8$^\circ$ from the LOS" (Introduction) [from (cite: 2016PASJ...68...69M; 2017ApJ...849...23M)]
- External data: Dust opacity model kappa=0.90 (nu/230 GHz)^beta cm2/g  
  > "we adopted $\kappa_{\nu}$ = 0.90$\times$($\nu$/230 GHz)$^{\beta}$ cm$^2$ g$^{-1}$" (Dust continuum emission) [from (cite: 1994A&A...291..943O)]

## Processing

### Calibration

- pipeline or manual: standard ALMA calibration  
  > "The data were calibrated in the standard manner of ALMA by using the CASA software package version 5.3.0" (Observation and reduction)
- casa version: CASA 5.3.0  
  > "CASA software package version 5.3.0" (Observation and reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1733-1304  
  > "absolute flux scaling using the quasar J1733–1304 ($\sim$10%)" (Observation and reduction)
- flux scale uncertainty: ~10%  
  > "we adopt 10% error for all the fluxes and/or brightness temperature" (Observation and reduction)
- self calibration: none  
  > "No self-calibration was performed." (Observation and reduction)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: 10 sigma cutoff on integrated line image  
  > "We adopted the cutoff signal-to-noise ratio of 10$\sigma$ ($\pm$ 75 K) for the integrated flux image." (CH3OH lines and infalling rotating envelope)
- multiscale scales: _not stated_
- continuum subtraction: line subtraction before integrating four sub-bands  
  > "We integrated all the four sub-bands for the dust continuum analysis after the line subtraction." (Observation and reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: circular 0.050x0.050 arcsec for continuum  
  > "reconstructed by using the circular beam of 0$''$.050 $\times$ 0$''$.050 as in the previous study" (Observation and reduction)
- final rms: 2.7 K continuum; 7.5 K (1.1 mJy/beam) stacked lines  
  > "The final image noise level (1$\sigma$) is 2.7 K for the continuum, and 7.5 K for line emission" (Observation and reduction)

### Inherited from earlier work

- circular 0.05 arcsec beam for continuum image  
  > "circular beam of 0$''$.050 $\times$ 0$''$.050 as in the previous study (cite: 2017ApJ...849...23M)" (Observation and reduction) [from (cite: 2017ApJ...849...23M)]
- infalling rotating envelope kinematic model  
  > "We used the kinematic model of the infalling rotating envelope developed for the low-mass protostars (cite: 2014Natur.507...78S; 2016ApJ...824...88O)" (CH3OH lines and infalling rotating envelope) [from (cite: 2014Natur.507...78S; 2016ApJ...824...88O)]

### Not stated but needed to reproduce (our reading)

- tclean parameters (weighting/robust, deconvolver, cell, image size, masks)
- line-free channels for continuum subtraction
- calibrator list other than flux calibrator and pipeline version
- line stacking procedure details (velocity alignment, weighting)
- flaring angle and model fit procedure (done by eye)
- elliptical Gaussian fit procedure
- RADEX input details beyond T and linewidth

## Analysis recipe

1. **Fit and subtract compact continuum, derive spectral index**: Elliptical Gaussian fit of compact emission, subtracted from image; spectral index from 45 and 150 GHz total fluxes  
  > "we performed the elliptical Gaussian fitting for the compact dust continuum emission, and then, the best-fit Gaussian was subtracted from the original image" (Dust continuum emission)
   - fitting: _not stated_
   - validation: Compact emission consistent with 45 GHz continuum  
  > "The compact emission is consistent with the continuum emission at 45 GHz previously reported" (Dust continuum)
2. **Optical depth, surface density and mass of dust**: Planck function fit to fluxes and sizes at 45 and 150 GHz for compact part; pixel-by-pixel tau=ln(Tdust/(Tdust-TB)) with power-law Tdust for resolved ring; Sigma=tau/kappa*Rgd  
  > "We, then, calculated $\tau_{\nu}$ from the ratio between $T_{\rm dust}$ and observed $T_{\rm B}$ in the resolved structure pixel-by-pixel" (Dust continuum emission)
   - parameter: T80au = 360 K  
  > "The referenced temperature $T_{\rm 80 au}$ was determined as 360 K" (Dust continuum emission)
   - assumption: beta=1, kappa150=0.59 cm2/g, gas-to-dust 100, Tdust ∝ r^-0.4  
  > "The assumed power-law index of -0.4 is a typical value for the embedded disk" (Dust continuum emission)
   - fitting: _not stated_
   - validation: beta=2 alternative tested  
  > "if $\beta$ = 2 is adopted, the dust mass opacity $\kappa_{\nu}$ becomes 40% smaller." (Gravitational stability of the disk)
3. **Envelope kinematics from CH3OH**: Stack hot CH3OH lines, make PV diagram, compare with infalling rotating envelope model with fixed l and enclosed mass  
  > "The specific angular momentum $l$ is also fixed to 2.4$\times$10$^{21}$ cm$^{2}$ s$^{-1}$, in order to have the centrifugal radius of 250 au" (CH3OH lines and infalling rotating envelope)
   - software: CASA
   - parameter: M_in = 12 Msun; inclination 8 deg; flaring angle ~35 deg  
  > "$M_{\rm in}$ is the enclosed mass that is fixed to 12 M$_{\ensuremath{\odot}}$" (CH3OH lines and infalling rotating envelope)
   - assumption: axisymmetric counterclockwise rotation, no outflow contribution  
  > "We assume that the envelope is rotating counterclockwise and purely axisymmetric." (CH3OH lines and infalling rotating envelope)
   - fitting: No formal fit; model compared qualitatively  
  > "further fine-tuned model fitting is beyond the scope of this study" (CH3OH lines)
   - validation: _not stated_
4. **Envelope mass from line ratio**: Non-LTE radiative transfer for lower-limit n and N(CH3OH); 12C/13C~60; abundance 1e-6  
  > "By using the non-local thermodynamic equilibrium radiative transfer code (cite: 2007A&A...468..627V), we estimated the lower-limit density" (CH3OH lines)
   - software: RADEX (van der Tak 2007)
   - parameter: Tkin=100 K, linewidth 5 km/s  
  > "we adopted a kinematic temperature of 100 K and velocity dispersion of 5 km s$^{-1}$" (CH3OH lines)
   - fitting: _not stated_
   - validation: Comparable to dust mass ~5 Msun  
  > "This is comparable with that estimated from the dust emission" (CH3OH lines)
5. **Infall/accretion rate, age, Toomre Q, clumps**: Infall time from equation of motion; Q=cs*kappa/(pi G Sigma) with Keplerian 10 Msun; clumps from Sigma>1e25 cm-2  
  > "Toomre’s $Q$ parameter is expressed as, $$\begin{eqnarray*} Q = \frac{c_{\rm s}\kappa}{\pi G\Sigma}, \end{eqnarray*}$$" (Toomre's Q parameter)
   - assumption: 50% of accreting mass goes to outflow  
  > "because 50% of accreting mass could be converted to the outflow in case of high-mass star-formation" (Accretion rate)
   - fitting: _not stated_
   - validation: Compared with simulations of Meyer et al. 2018  
  > "The latter value is comparable to that reported in (cite: 2018MNRAS.473.3615M) again." (Gravitational stability)

## Software

- **CASA** 5.3.0: calibration and imaging  
  > "CASA software package version 5.3.0" (Observation and reduction)
- **RADEX** : non-LTE radiative transfer of CH3OH (cited as van der Tak 2007; name not given in text)  
  > "non-local thermodynamic equilibrium radiative transfer code (cite: 2007A&A...468..627V)" (CH3OH lines)
- **PyFITS** : listed software  
  > "PyFITS (cite: 1999ASPC..172..483B)" (Software)
- **Matplotlib** : listed software (plotting)  
  > "Matplotlib (cite: 2007CSE.....9...90H)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Spectral index 45-150 GHz | 2.5 | 0.2 | dimensionless | 1 | The spectral index is 2.5 ± 0.2 between 45 and 150 GHz |
| Compact component optical depth at 150 GHz | 2.0 | +1.4/-0.9 | dimensionless | 2 | 2.0$^{+1.4}_{-0.9}$ |
| Total mass of dusty accretion system (beta=1) | 1.9 | +1.0/-0.8 | Msun | 2 | The total mass of the dusty accretion system is 1.9$^{+1.0}_{-0.8}$ M$_{\odot}$ |
| Disk outer radius | 250 | not stated | au | 1 | outer radius of 250 au |
| Envelope mass from CH3OH | 7 | not stated | Msun | 4 | We finally obtained a total envelope mass of 7 M$_{\ensuremath{\odot}}$ |
| Accretion rate onto star | 3e-3 or higher | not stated | Msun/yr | 5 | 3$\times$ 10$^{-3}$ M$_{\odot}$ yr$^{-1}$ or higher |
| Minimum Toomre Q (beta=1) | 0.9 | not stated | dimensionless | 5 | the minimum $Q$ reaches 0.9 around the eastern local peak |
| Minimum Q (beta=2) | 0.4 | not stated | dimensionless | 5 | Recalculated $Q$ values are 0.9 (average), 0.4 (minimum), and 2.0 (maximum) |
| Clump masses (beta=1) | 0.04 and 0.09 | not stated | Msun | 5 | The clump masses were estimated to be 0.04 and 0.09 M$_{\ensuremath{\odot}}$ |

## Qualitative findings

- Asymmetric, clumpy ring-like disk structure may trace spiral arm and/or fragmentation  
  > "Observed asymmetric and clumpy structures could trace a spiral arm and/or disk fragmentation." (abstract)

## Claim tuples

- H: The disk around G353 is gravitationally unstable | E: Dust-continuum mass and Toomre Q map | R: Q typically 1-2, minimum 0.9 (beta=1) to 0.4 (beta=2) | F: Disk is self-gravitating and unstable | **supported**
- H: The disk radius matches the centrifugal radius of the envelope | E: Infalling rotating envelope model on CH3OH PV diagram | R: l=2.4e21 cm2/s gives ~250 au | F: Dust disk is a centrifugal disk | **supported**
- H: G353 is very young | E: Infall rate from envelope mass and infall time | R: 3e-3 Msun/yr | F: Age well below 1e4 yr | **supported**
- H: Angular momentum is removed in the disk | E: Compare envelope l with inner streams | R: Envelope l four times larger | F: 70% removed via gravitational torque | **partially**

## Reasoning

- Why this data: Nearly face-on geometry allows direct imaging of radial structure  
  > "G353 is the best target for direct imaging of any radial structures in the disk" (Introduction)
- Why this method: _not stated_
- Alternative: Tidal perturbation by a cluster member rejected since no bright member in FOV  
  > "this is unlikely to be the case because no bright cluster member was detected in the ALMA FOV" (Gravitational stability)
- How they decided it was enough: _not stated_
- Limitation (authors): Beta uncertainty dominates Q; kinematic model not finely fitted; larger-scale envelope resolved out  
  > "The major uncertainty of $Q$ in this study originates from the uncertainty of the dust opacity index $\beta$" (Gravitational stability)
- Caveat (inferred, ours): Single 5-minute single-band observation; beta degenerate with mass and Q
- Caveat (inferred, ours): Dust temperature profile assumed, not measured
- Caveat (inferred, ours): Kinematic model not fitted, only visually compared
- Caveat (inferred, ours): Line optical depth/temperature assumptions yield only lower limits
- Caveat (inferred, ours): Q values exceed refined fragmentation criteria for beta=1

## Reproducibility

- Data public (paper): ALMA dataset 2016.1.01068.S cited  
  > "This work makes use of the ALMA dataset ADS$/$JAO.ALMA$\#$2016.1.01068.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: tclean settings
- Missing: line-free channels
- Missing: stacking details
- Missing: model flaring/PV comparison details
- Missing: 45 GHz JVLA data
- Data volume (inferred): ~10-50 GB (one short long-baseline Band 4 execution)
- Score (inferred): 3/5, Data public and recipe moderately described, but imaging parameters and model comparison details are missing.
- Rediscovery candidate: no, Imaging settings unstated and the kinematic model comparison is qualitative, though the main continuum numbers are derivable.

## Links

- Method: (cite: 2014Natur.507...78S; 2016ApJ...824...88O) (infalling rotating envelope model)
- Companion: (cite: 2017ApJ...849...23M) (previous 45 GHz JVLA study of G353)

## Checks

```json
{
 "quotes": 70,
 "quotes_ok": 70,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 50,
  "rate": 0.649
 },
 "evidence_ok": true
}
```
