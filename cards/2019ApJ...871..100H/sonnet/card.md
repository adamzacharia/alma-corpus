# ALMA Observations of the Protostellar Disk around the VeLLO IRAS 16253-2429

`2019ApJ...871..100H` | The Astrophysical Journal 2019 | first author: Hsieh, Tien-Hao | arXiv: 1811.11651 | DOI: 10.3847/1538-4357/aaf4fe

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, protoplanetary_disks
- Question: Is there a disk around the VeLLO IRAS 16253, and what are its dust, kinematic and chemical (CO freeze-out) properties?  
  > "We aim to search for a disk around this unique source and study its physical and chemical properties." (INTRODUCTION)
- Target **IRAS 16253-2429**: coordinates RA 16h28m21.6s, Dec -24d36m23.4s  
  > "toward IRAS 16253 ($\alpha$=16$^{\rm h}$28$^{\rm m}$21.6s, $\delta$=$-$24$^\circ$36$'$23.4$''$)" (Observations); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.00598.S, 2015.1.00741.S, 2013.1.00879.S
- bands: _not stated_
- frequencies and spectral setup: channel width 122 kHz (0.16 km/s) CO, 61 kHz (0.08 km/s) C18O  
  > "The channel width was 122 kHz (0.16 km s$^{-1}$) for CO ($2-1$) and 61 kHz (0.08 km s$^{-1}$) for C$^{18}$O ($2-1$)." (Observations)
- continuum bandwidth: 1840 MHz centered at 217 GHz (1.38 mm)  
  > "The continuum bandwidth was 1840 MHz, centered at 217 GHz (1.38 mm)." (Observations)
- arrays: _not stated_
- configurations: C40-7, 42 antennas  
  > "The data were obtained in configuration of C40-7 with a projected baseline range of 11 to 2629 k$\lambda$" (Observations)
- baselines: _not stated_
- angular resolution: 0.11"x0.08" continuum (uniform); 0.14"x0.11" CO (natural)  
  > "resulting in a spatial resolution of $0.11\ensuremath{''}\times0.08\ensuremath{''}$ with uniform weighting for the continuum" (Observations)
- max recoverable scale: _not stated_
- sensitivity: rms 0.066 mJy/beam continuum; 5.6 (CO) and 4.9 (C18O) mJy/beam per 0.16 km/s channel  
  > "The rms noise level is 0.066 mJy beam$^{-1}$ for the continuum map, and 5.6 and 4.9 mJy beam$^{-1}$ for the CO and C$^{18}$O maps" (Observations)
- time on source: 48 min total, ~20 min on source  
  > "The total observing time was 48 min and the on-source time was $\approx$20 min." (Observations)
- observing dates: 2017 Aug 18  
  > "on 2017 Aug 18th (Cycle 4 project, 2016.1.00598.S)" (Observations)
- pi or archival as stated: 0.87 mm data archival (PI L. Looney); C18O combined with Cycle 2 data of Yen et al. 2017  
  > "The C$^{18}$O ($2-1$) data were combined with the ALMA cycle 2 data from (cite: ye17) to increase the sensitivity." (Observations)
- Line: CO 2-1 (not stated)
- Line: C18O 2-1 (not stated)
- External data: Cycle 2 C18O (2-1) ALMA data combined with new data  
  > "The C$^{18}$O ($2-1$) data were combined with the ALMA cycle 2 data from (cite: ye17) to increase the sensitivity." (Observations) [from (cite: ye17)]
- External data: Cloud core rotation rate used for disk growth estimate  
  > "If we use $\Omega=\rm 1.8-2.1\times10^{-14}~rad~s^{-1}$ (cite: to11) and $a=0.14~\rm km~s^{-1}$ (cite: hs18)" (The disk size and disk growth) [from (cite: to11), (cite: hs18)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1733-1304 (bandpass J1517-2422, phase J1625-2527)  
  > "The bandpass, flux, and phase calibrators were J1517-2422, J1733-1304, and J1625-2527, respectively." (Observations)
- flux scale uncertainty: _not stated_
- self calibration: not applied  
  > "Self-calibration is not applied in order to maintain astrometric information of the source." (Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: uniform for continuum, natural for CO  
  > "with uniform weighting for the continuum and of $0.14\ensuremath{''}\times0.11\ensuremath{''}$ with natural weighting for CO ($2-1$)" (Observations)
- uv taper: C18O: uv-distance <600 kλ, beam 0.40"x0.37"  
  > "we selected data with a $uv$-distance shorter than 600 k$\lambda$, resulting in a relatively Gaussian-like beam with a size of $0.40\ensuremath{''}$ by $0.37\ensuremath{''}$" (Observations)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: C18O combined with Cycle 2 data  
  > "The C$^{18}$O ($2-1$) data were combined with the ALMA cycle 2 data from (cite: ye17) to increase the sensitivity." (Observations)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Torus-like thick disk density model  
  > "we adopted the torus-like disk model from (cite: le17a; le17b) by adding an exponentially decreasing scale height beyond a radius $R_{\rm t}$" (Model B1/B2 - Thick-disk model) [from (cite: le17a; le17b)]
- PV model radiative transfer code, temperature/density structure  
  > "We use the radiative transfer code from (cite: le14) to perform the PV model given temperature and density structures under local thermodynamic equilibrium (LTE) conditions." (PV-diagram and dynamic model) [from (cite: le14)]
- Chi-squared in complex visibility space  
  > "The $\chi^2$ is calculated in the complex space (i.e. Eq. 2 in (cite: as17))" (Models of the continuum images) [from (cite: as17)]

### Not stated but needed to reproduce (our reading)

- CASA version and whether the pipeline or manual calibration was used
- Imaging task, deconvolver, cleaning masks, cell/image size, continuum-subtraction channels
- Flux scale uncertainty
- Model grid ranges and step sizes for continuum and PV fits
- Dust composition/opacity inputs to the DIANA tool
- Distance adopted
- Details of the Cycle 2 C18O data processing and project-code association (2013.1.00879.S)
- Priors and sampling or minimization method for the chi-squared fits
- PV cut widths and position angles

## Analysis recipe

1. **Fit continuum visibilities with double Gaussian**: Double Gaussian fit to visibility amplitudes at 0.87 and 1.38 mm, finding a break at ~200 kλ between extended and compact components  
  > "We employ a double Gaussian fit to the observed amplitude but not phase, and we find a break point at a $uv$-distance of $\approx$200 k$\lambda$" (continuum emission at 0.87 mm and 1.38 mm)
   - fitting: _not stated_
   - validation: Check sources compared to reference positions (within 10 mas at 1.3 mm, 5 mas at 0.87 mm)  
  > "find that they are consistent with the referenced positions within 10 mas and 5 mas, respectively" (continuum emission at 0.87 mm and 1.38 mm)
2. **Model continuum offset with radiative transfer**: RADMC-3D flared disk (A) and torus-like thick disk (B1/B2) grids, chi2 fit to visibilities beyond 200 kλ using vis_sample  
  > "We construct model grids (Sections [4.1.1](#sec:modA) and [4.1.2](#sec:modB)) to perform a $\chi^2$ fitting to the visibilities at uv-distances beyond 200 k$\lambda$." (Models of the continuum images)
   - software: RADMC-3D, DIANA Opacity Tool, vis_sample
   - parameter: Model A free parameters: Lstar, Mdisk, Rdisk, theta_flared, a_pow, a_max; r0 = 25 au  
  > "We take six free parameters including the protostellar luminosity ($L_{\rm star}$), $M_{\rm disk}$ (total mass of the disk scaled by $\Sigma_0$), $R_{\rm disk}$, $\theta_{\rm flared}$, $a_{\rm pow}$, and $a_{\rm max}$." (Model A - flared-disk model)
   - assumption: Inclination 65 deg from Gaussian aspect ratio; center, PA fixed from 1.38 mm fit; grain size distribution n(a) ∝ a^-a_pow  
  > "an inclination angle of $65\ensuremath{^\circ}$ is estimated from the Gaussian aspect ratio" (Model A - flared-disk model)
   - fitting: chi-squared grid fit; errors from chi2 distribution at 99.9% confidence  
  > "The error of the fitted parameters are calculated with the $\chi^2$ distribution in a confidence level of 99.9%." (Table 2)
   - validation: Compare model peak offset with observed 46 mas  
  > "the offset (7 mas) in this model is still much smaller than the observed one (46 mas)" (Model A - flared-disk model)
3. **Model CO/C18O PV diagrams**: Rotating infalling envelope model with conserved angular momentum and free-fall, LTE radiative transfer, chi2 over major and minor axis PV cuts  
  > "We model the PV diagrams assuming a rotating infalling envelope with conservation of angular momentum." (PV-diagram and dynamic model)
   - software: Lee et al. 2014 radiative transfer code
   - parameter: Free: rho0, p, theta_flared, V_rot,0, V_infall,0, F_C18O; C18O fit at |V-Vlsr|<1.6 km/s, CO at >1.6 km/s  
  > "$\mid V-V_{\rm lsr} \mid<1.6$ km s$^{-1}$ for C$^{18}$O and $\mid V-V_{\rm lsr} \mid>1.6$ km s$^{-1}$ for CO" (PV-diagram and dynamic model)
   - assumption: X_CO=5e-4, X_CO/X_C18O=560, T0=70 K, T ∝ r^-0.4  
  > "We take the CO abundance relative to H$_2$ as $X_{\rm CO}=5\times10^{-4}$ and the C$^{18}$O isotopic ratio of $X_{\rm CO}/X_{\rm C^{18}O}=560$ (cite: wi94)." (PV-diagram and dynamic model)
   - fitting: chi-squared minimization; modeled images convolved with the beam  
  > "we convolve the modeled images with the beam of the observations and make the PV diagrams with the same PV cuts" (PV-diagram and dynamic model)
   - validation: _not stated_
4. **CO channel-map model with CO depletion**: Compare best-fit dynamic model with channel maps via vis_sample, per-channel intensity scaling, add f_snow zeroing gas below f_snow×H  
  > "the gas density at $z<f_{\rm snow}\times H(R)$ is set to zero, with $f_{\rm snow}$ between 0 (no CO depletion) and 1 (complete CO depletion)" (CO channel map and CO-depletion model)
   - software: vis_sample
   - fitting: best f_snow = 0.55, chi2_r 1.78 vs 1.92 for f_snow=0  
  > "we find the best-fit CO-depletion model for $f_{\rm snow}=0.55$ with $\chi^2_{\rm r}=1.78$ while $\chi^2_{\rm r}=1.92$ for $f_{\rm snow}=0$" (CO channel map and CO-depletion model)
   - validation: Qualitative reproduction of quadruple pattern; chi2 difference small  
  > "The model with CO depletion reproduces the quadruple pattern qualitatively well, though the CO peak positions are not perfectly matched and the difference between the $\chi^2_{\rm r}$ is small." (CO channel map and CO-depletion model)

## Software

- **RADMC-3D** : Monte Carlo radiative transfer for continuum disk models  
  > "we model the emission using the Monte Carlo radiative transfer code RADMC-3D" (Models of the continuum images)
- **DIANA Opacity Tool** : Dust opacity as function of wavelength  
  > "The dust opacity $\kappa$ as a function of wavelength is constructed using DIANA Opacity Tool" (Models of the continuum images)
- **vis_sample** : Compute model visibilities from synthetic images  
  > "the modeled visibilities are computed from the synthetic images using vis_sample" (Models of the continuum images)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 1.3 mm deconvolved Gaussian size | 0.16" x 0.07" (20 au x 8.8 au) | not stated | arcsec | 1 | The 1.3 mm dust continuum emission has a deconvolved Gaussian size of $0.16\ensuremath{''}\times0.07\ensuremath{''}$ (20 au $\times$ 8.8 au) |
| Offset between 0.87 and 1.38 mm peaks | 46 | not stated | mas | 1 | the central positions are offset by 46 milliarcsecs (mas) |
| Disk component flux 1.38 mm | 10.1 | 0.4 | mJy | 1 | 10.1$\pm$0.4 |
| Best-fit CO depletion parameter f_snow | 0.55 | not stated | dimensionless | 4 | we find the best-fit CO-depletion model for $f_{\rm snow}=0.55$ |
| Central mass from free-fall | 0.028 | not stated | Msun | 3 | we estimate a central mass of $\sim$$0.028~M_\odot$ |
| Central mass from Keplerian rotation | 0.12 | not stated | Msun | 4 | We then estimate a mass of the central star of 0.12 $M_\odot$ |
| Best-fit V_rot,0 and V_infall,0 | 1.6 and 1.4 | not stated | km/s | 3 | $V_{\rm rot,0}=1.6~\rm km~s^{-1}$, and $V_{\rm infall,0}=1.4~\rm km~s^{-1}$ |
| Model A disk mass | 1.6e-3 | 0.1e-3 | Msun | 2 | 1.6$\pm$0.1 |

## Qualitative findings

- Source remains single at ~0.1" resolution  
  > "These images indicate that IRAS 16253 remains a single source at $\approx0.1\ensuremath{''}$ resolution." (continuum emission at 0.87 mm and 1.38 mm)

## Claim tuples

- H: The compact continuum component traces a disk | E: Double Gaussian visibility fit at two wavelengths | R: Consistent PA and aspect ratio, minor axis aligned with outflow | F: Compact component likely traces a disk | **supported**
- H: The 0.87/1.38 mm offset comes from optical depth differences | E: RADMC-3D flared and thick-disk models | R: Models give 7-20 mas offsets vs 46 mas observed | F: Optical depth can contribute but does not fully explain it | **partially**
- H: A Keplerian disk is present and formed from a first core | E: PV and channel map modeling of CO and C18O | R: Centrifugal radii 16-64 au give Keplerian disk radius of 8-32 au | F: Disk too large for slow-start growth, favoring early-start | **partially**
- H: CO freeze-out explains the quadruple CO pattern | E: Add f_snow depletion to channel map model | R: chi2_r 1.78 vs 1.92 | F: CO depletion plausible but not uniquely established | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Proper motion and phase calibration error as causes of the offset were considered but not excluded; dust absorption and CO self-absorption rejected for the quadruple pattern  
  > "The second hypothesis is also unlikely because the far side (or bottom side) should be much fainter than the near side by being obscured." (CO channel map and CO-depletion model)
- How they decided it was enough: _not stated_
- Limitation (authors): Offset smaller than beam; calibration issue or proper motion not excluded  
  > "the offset of $0.046\ensuremath{''}$ is smaller than the beam sizes, $0.15\ensuremath{''}$ at 0.87 mm and $0.1\ensuremath{''}$ at 1.38 mm" (grain growth at the Class 0 stage)
- Caveat (inferred, ours): Offset of 46 mas below beam size and 0.87 mm phase calibration uncertain
- Caveat (inferred, ours): Large F_C18O=52 scaling factor undermines abundance-based interpretation
- Caveat (inferred, ours): Small chi2 improvement for CO depletion
- Caveat (inferred, ours): Keplerian disk radius is speculative range, not a direct measurement
- Caveat (inferred, ours): Assumed T0 and 1/r rotation profile fixed

## Reproducibility

- Data public (paper): Archival 0.87 mm data obtained from ALMA archive  
  > "we obtained 0.87 mm data from the ALMA archive (2015.1.00741.S, PI: L. Looney)" (Observations)
- Products in archive: _not stated_
- Missing: CASA/pipeline version and imaging parameters
- Missing: Model grid definitions
- Missing: Custom PV modeling code (Lee et al. 2014) details
- Data volume (inferred): ~50-100 GB raw for three projects
- Score (inferred): 5/5, Data public and fitting approach described, but processing and grid details not given.
- Rediscovery candidate: no, Imaging settings and custom modeling details missing; results depend on bespoke models.

## Links

- Method: (cite: le14) (PV model radiative transfer code)
- Method: (cite: wa16) (DIANA opacity tool)
- Companion: (cite: ye17) (Cycle 2 C18O data and prior infall analysis)
- Companion: (cite: hs18) (Past accretion burst and CO snow line)

## Checks

```json
{
 "quotes": 59,
 "quotes_ok": 59,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 41,
  "rate": 0.586
 },
 "evidence_ok": true
}
```
