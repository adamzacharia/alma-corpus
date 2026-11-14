# A Keplerian disk around a Class 0 source: ALMA observations of VLA1623A

`2013A&A...560A.103M` | Astronomy and Astrophysics 2013 | first author: Murillo, Nadia M. | arXiv: 1310.8481 | DOI: 10.1051/0004-6361/201322537

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: Is the C18O emission around the Class 0 source VLA1623A tracing a rotationally supported (Keplerian) disk rather than a pseudo-disk/infall structure?  
  > "In order to determine whether the C$^{18}$O emission is tracing a rotationally supported disk about VLA1623A, we perform Position-Velocity diagram analysis and models of the C$^{18}$O emission" (Introduction)
- Target **VLA1623A (also VLA1623B, VLA1623W)**: coordinates 16:26:26.390 -24:24:30.688 (VLA1623A)  
  > "| VLA1623A | 16:26:26.390 | -24:24:30.688 | 93.1 | 201.3$\pm$1.2 |" (Table 1); "located in $\rho$ Ophiuchus ($d \sim$ 120pc, (cite: loinard2008))" (Introduction); z/distance d ~ 120 pc  
  > "| VLA1623A | 16:26:26.390 | -24:24:30.688 | 93.1 | 201.3$\pm$1.2 |" (Table 1); "located in $\rho$ Ophiuchus ($d \sim$ 120pc, (cite: loinard2008))" (Introduction); distance from Loinard et al. 2008  
  > "| VLA1623A | 16:26:26.390 | -24:24:30.688 | 93.1 | 201.3$\pm$1.2 |" (Table 1); "located in $\rho$ Ophiuchus ($d \sim$ 120pc, (cite: loinard2008))" (Introduction)

## Data provenance

- ALMA projects: 2011.0.00902.S
- bands: Band 6 (230 GHz)  
  > "Observations were done in Band 6 (230 GHz) using the extended configuration" (Observations)
- frequencies and spectral setup: four lines DCO+ (3-2), C18O (2-1), N2D+ (3-2), 12CO (2-1) plus continuum  
  > "The spectral configuration was set-up to observe four molecular lines: DCO$^{+}$ (3-2), C$^{18}$O (2-1), N$_{2}$D$^{+}$ (3-2) and $^{12}$CO (2-1), in addition to continuum." (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: extended configuration, 16 antennae, max baseline ~400 m  
  > "consisting of 16 antennae with a maximum baseline of $\sim$400m" (Observations)
- baselines: _not stated_
- angular resolution: 0.79" x 0.54" continuum; 0.79" x 0.61" C18O  
  > "The synthesized beam size is 0.79$\ensuremath{''}$ $\times$ 0.54$\ensuremath{''}$ for continuum and 0.79$\ensuremath{''}$ $\times$ 0.61$\ensuremath{''}$ for C$^{18}$O" (Observations)
- max recoverable scale: _not stated_
- sensitivity: C18O rms noise = 18 mJy/beam; velocity resolution 0.0833 km/s  
  > "our ALMA observations have higher sensitivity (rms noise = 18 mJy beam$^{-1}$) and velocity resolution (0.0833 km s$^{-1}$)" (3.2 C18O (2-1))
- time on source: 1 hour total observing time, duty cycle 58%  
  > "for a total observing time of 1 hour and a duty cycle of 58%" (Observations)
- observing dates: April 8th, 2012  
  > "during the Early Science Cycle 0 period on April 8th, 2012" (Observations)
- pi or archival as stated: _not stated_
- Line: C18O 2-1 (not stated)
- Other facility **SMA**: earlier 1.3 mm continuum and C18O/C17O data used for comparison  
  > "We compare the ALMA 1.3 mm continuum flux with that obtained with SMA for the same wavelength reported in (cite: murillo2013)." (Observations)
- Other facility **JCMT**: single-dish C18O (2-1) flux for recovered-flux comparison  
  > "JCMT observations towards VLA1623 by (cite: jorgensen2002) detected C$^{18}$O (2-1) with a flux of 12.1 K km s$^{-1}$" (Observations)
- External data: JCMT C18O (2-1) flux 12.1 K km/s (174 Jy km/s)  
  > "JCMT observations towards VLA1623 by (cite: jorgensen2002) detected C$^{18}$O (2-1) with a flux of 12.1 K km s$^{-1}$ (174 Jy km s$^{-1}$, with 14.46 Jy/K)." (Observations) [from Jørgensen et al. 2002 (cite: jorgensen2002)]
- External data: systemic velocity 3.4-3.8 km/s  
  > "(cite: mardones1997) and (cite: yu1997) report VLA1623’s systemic velocity $v_{\rm lsr}$ to be between 3.4 to 3.8 km s$^{-1}$." (3.2 C18O (2-1)) [from Mardones et al. 1997; Yu & Chernin 1997]
- External data: 84 deg misalignment between magnetic field and rotation axis  
  > "given VLA1623A’s misalignment of 84$^{\circ}$ between magnetic field direction and rotational axis (cite: hull2013)" (5 Discussion) [from Hull et al. 2013]

## Processing

### Calibration

- pipeline or manual: re-did calibration with standard pipeline for single pointing observations  
  > "We re-did the data calibration and reduction using the standard pipeline for single pointing observations." (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: no; recalibrated, consistent with delivered continuum flux  
  > "Comparison of the delivered data and our recalibrated data shows consistency in continuum flux levels." (Observations)
- flux calibrator: Titan (flux), 3C 279 (bandpass), 1733-130 (gain)  
  > "Calibration was done with 3C 279, 1733-130 and Titan for bandpass, gain and flux calibration, respectively." (Observations)
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
- final beam: 0.79"x0.54" continuum; 0.79"x0.61" C18O  
  > "The synthesized beam size is 0.79$\ensuremath{''}$ $\times$ 0.54$\ensuremath{''}$ for continuum and 0.79$\ensuremath{''}$ $\times$ 0.61$\ensuremath{''}$ for C$^{18}$O" (Observations)
- final rms: 18 mJy/beam (C18O)  
  > "rms noise = 18 mJy beam$^{-1}$" (3.2 C18O (2-1))

### Inherited from earlier work

- UV-space PV diagram method (channel-by-channel visibility fitting)  
  > "UV-space PV diagrams, on the other hand, are constructed by fitting, channel by channel, the UV visibilities of the line emission to find the peak position in each channel (cite: lommen2008; jorgensen2009)." (4.1 Position-Velocity Diagrams) [from (cite: lommen2008; jorgensen2009)]
- centrifugal radius vs time equation  
  > "To calculate the time since collapse for $R_{\rm c}$ = 150 AU, we use the equation from (cite: belloche2013)" (5 Discussion) [from (cite: belloche2013)]

### Not stated but needed to reproduce (our reading)

- CASA version and pipeline version
- imaging parameters (tclean/clean weighting, robust, cell, image size, masks)
- continuum subtraction and line-free channels
- how the flux scale uncertainty was handled
- UV-fitting details (software, uncertainties) for the PV diagram
- thin-disk model code availability, temperature gradient and column density values
- exact definition of the residual criterion for best-fit model
- rest frequency used for C18O

## Analysis recipe

1. **Measure continuum fluxes and compare with SMA**: Integrated continuum emission over source-sized region to 3 sigma; imstat comparison with SMA for VLA1623B  
  > "Integrated fluxes for each source were obtained by integrating the continuum emission over a region the size of the source out to 3$\sigma$." (3.1 1.3 mm Continuum)
   - software: CASA
   - fitting: _not stated_
   - validation: ALMA VLA1623B 96.3 mJy vs SMA 96.8 mJy consistent  
  > "for the ALMA data, VLA1623B has an integrated flux of 96.3$\pm$0.7 mJy. This shows that both observations are consistent." (Observations)
2. **Image-space and UV-space PV diagrams**: PV diagram along major axis (PA 35 deg); UV-space peak positions per channel rotated, fit with power law v=aR^n in log-log; red-shifted points v>5.0 km/s only  
  > "The data points are fit with a power law of the form $v = aR^{n}$ and we find that the UV-space PV diagram is independent of the inclination angle of the structure." (4.1 Position-Velocity Diagrams)
   - parameter: vlsr range 3.4-4.0 km/s, mean 3.7 used  
  > "which uses the mean $v_{\rm lsr}$, 3.7 km s$^{-1}$." (4.1 Position-Velocity Diagrams)
   - fitting: power law fit in log-log space  
  > "projected onto Position-Velocity space and fit with a power law in log-log space" (4.1 Position-Velocity Diagrams)
   - validation: fits for any vlsr within error  
  > "The results of the fit for any $v_{\rm lsr}$ are within the error of the fit presented here" (4.1 Position-Velocity Diagrams)
3. **Thin disk kinematic modelling of five cases with foreground absorption**: Analytical thin-disk model (no radiative transfer) with free fall, free fall+Keplerian, conserved AM, infall+Keplerian, Keplerian velocity fields; three Gaussian absorbing layers; compared via channel-map residuals  
  > "we proceed to further investigate the structure and its kinematics using an analytical thin disk model with the addition of absorbing foreground material." (4.2 Modelling of C18O (2-1))
   - parameter: M*=0.2 Msun, PA=35 deg, vlsr=4.0 km/s fixed; free: vwidth 0.1-1.0 km/s, i 0-90 deg, Rout 100-200 AU  
  > "The attempted value ranges for each parameter are: 0.1 km s$^{-1}$ $\leq$ $v_{\rm width}$ $\leq$ 1.0 km s$^{-1}$" (4.2 Modelling of C18O (2-1))
   - assumption: d=120 pc; optically thin emission, constant density, adjusted temperature gradient  
  > "we assume the observed emission is optically thin, and set the density as a constant and adjust the temperature gradient to match the observed spectral profile." (4.2 Modelling of C18O (2-1))
   - fitting: manual adjustment by eye then residuals; least residual deemed best  
  > "We deemed the model with the least residual the best fit (discarding the filaments to the north and south)." (4.2 Modelling of C18O (2-1))
   - validation: channel-map residuals for each model  
  > "Appendix [8](#seccomp) shows the channel map for each model, compared with observations and the corresponding residual." (4.2 Modelling of C18O (2-1))
4. **Estimate time since collapse for 150 AU disk**: Belloche (2013) Rc equation with Omega=4e-14 rad/s, a=0.2 km/s  
  > "we obtain $t$ = 8.5 $\times$ 10$^{5}$ yr for a centrifugal radius of 150 AU." (5 Discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : imstat for flux measurement  
  > "We use the same region and task (CASA’s imstat task) to measure the integrated flux for both datasets." (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| VLA1623A integrated 1.3 mm flux | 201.3 | 1.2 | mJy | 1 | / VLA1623A / 16:26:26.390 / -24:24:30.688 / 93.1 / 201.3$\pm$1.2 / |
| VLA1623B integrated flux | 96.3 | 0.7 | mJy | 1 | / VLA1623B / 16:26:26.309 / -24:24:30.588 / 93.5 / 96.3$\pm$0.7 / |
| Fraction of single-dish C18O flux recovered | ~8 | not stated | % | 0 | Thus, we recover $\sim$8% of the total single dish detected flux. |
| Power-law index of high-velocity UV PV points | -0.5 | 0.08 | dimensionless | 2 | well fit by $v \propto R^{-0.5 \pm 0.08}$, giving a central protostellar mass of $M_{*}$ of 0.22$\pm$0.02 M$_{\ensuremath{\odot}}$ |
| Central protostellar mass | 0.22 | 0.02 | Msun | 2 | giving a central protostellar mass of $M_{*}$ of 0.22$\pm$0.02 M$_{\ensuremath{\odot}}$ |
| Disk position angle | 35 | 15 | deg | 2 | major axis (PA = 35$\pm$15$^{\circ}$) |
| Best-fit inclination | 55 | not stated | deg | 3 | $i$ = 55$^\circ$ and $R_{\rm out}$ = 180 AU |
| Disk outer radius | 180 | not stated | AU | 3 | $i$ = 55$^\circ$ and $R_{\rm out}$ = 180 AU |
| Keplerian extent (Rcrit) | 150 | not stated | AU | 3 | with the best fit having $R_{\rm crit}$ = 150 AU |
| Time since collapse for Rc=150 AU | 8.5e5 | not stated | yr | 4 | we obtain $t$ = 8.5 $\times$ 10$^{5}$ yr for a centrifugal radius of 150 AU. |

## Qualitative findings

- Filament-like C18O features north and south of the disk, possibly disk wind or outflow-entrained material  
  > "the high sensitivity allowed the detection of previously unknown filament-like features, located to the north and south of VLA1623A’s C$^{18}$O disk structure" (3.2 C18O (2-1))

## Claim tuples

- H: Class 0 source VLA1623A hosts a rotationally supported Keplerian disk | E: PV diagrams and thin-disk models of ALMA C18O (2-1) | R: v ∝ R^-0.5±0.08 for high velocities; Keplerian or infall+Keplerian with Rcrit=150 AU fit best; M*=0.22 Msun | F: Emission traces a Keplerian disk out to 150 AU | **supported**
- H: Free fall or conserved angular momentum explain the structure | E: Modelled these cases and compared residuals | R: Free fall gives gradient along outflow; conserved AM mismatches blue peak | F: Both ruled out | **supported**
- H: Weak, misaligned magnetic fields favour early disk formation | E: Comparison with literature polarization and models | R: Field misaligned by 84 deg and weak | F: Consistent with Krumholz et al. predictions | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Free fall, free fall+Keplerian (small Rcrit), conserved AM models rejected  
  > "It is clear that the pure free fall case does not fit the observed C$^{18}$O emission" (4.3 Model Results)
- How they decided it was enough: _not stated_
- Limitation (authors): Cannot distinguish infall+Keplerian from pure Keplerian in outer 30 AU due to low S/N; foreground absorption  
  > "This uncertainty is due to the low S/N ratio (5$\sigma$) in the outer edges of the observed disk structure" (5 Discussion)
- Caveat (inferred, ours): Model fits by eye without formal chi-square or uncertainties
- Caveat (inferred, ours): Foreground absorbers fitted ad hoc
- Caveat (inferred, ours): Optically thin assumption questionable given large opacities
- Caveat (inferred, ours): Only 8% of single-dish flux recovered

## Reproducibility

- Data public (paper): ALMA project 2011.0.00902.S named; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA# 2011.0.00902.S" (Acknowledgements)
- Products in archive: _not stated_
- Missing: thin-disk model code
- Missing: CASA version and imaging parameters
- Missing: UV fitting details
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, Single public dataset, but imaging settings and custom model code are not given and fitting is by eye.
- Rediscovery candidate: no, Model code and imaging details missing; the fits are qualitative.

## Links

- Method: Lommen et al. 2008; Jørgensen et al. 2009 (UV-space PV diagram method)
- Companion: Murillo & Lai 2013 (cite: murillo2013) (SMA observations of VLA1623)

## Checks

```json
{
 "quotes": 59,
 "quotes_ok": 59,
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
  "facts": 69,
  "stated": 40,
  "rate": 0.58
 },
 "evidence_ok": true
}
```
