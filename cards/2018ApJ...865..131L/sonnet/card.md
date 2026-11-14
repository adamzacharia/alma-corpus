# High-resolution ALMA Study of the Proto-brown-dwarf Candidate L328-IRS

`2018ApJ...865..131L` | The Astrophysical Journal 2018 | first author: Lee, Chang Won | arXiv: 1809.10466 | DOI: 10.3847/1538-4357/aadcf6

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: Is the proto-brown-dwarf candidate L328-IRS substellar? Measure its central mass via disk kinematics and refine the outflow inclination and mass accretion rate.  
  > "This paper presents our observational attempts to precisely measure the central mass of a proto-brown dwarf candidate, L328-IRS, in order to investigate whether L328-IRS is in the substellar mass regime." (abstract)
- Target **L328-IRS**: coordinates RA 18h16m59.4973s, Dec -18d02m30.263s (J2000, continuum center)  
  > "which corresponds to $\sim$87 AU $\times$ 37 AU in a linear size at its distance ($\sim 217$ pc, Maheswar et al. 2011)" (3.1 1.3mm continuum); "18^h16^m59.4973s\pm0.0002^s, -18^{\circ} 02\ensuremath{'} 30\ensuremath{''}.263\pm 0.001\ensuremath{''}" (Table 1); z/distance ~217 pc  
  > "which corresponds to $\sim$87 AU $\times$ 37 AU in a linear size at its distance ($\sim 217$ pc, Maheswar et al. 2011)" (3.1 1.3mm continuum); "18^h16^m59.4973s\pm0.0002^s, -18^{\circ} 02\ensuremath{'} 30\ensuremath{''}.263\pm 0.001\ensuremath{''}" (Table 1); distance from Maheswar et al. 2011  
  > "which corresponds to $\sim$87 AU $\times$ 37 AU in a linear size at its distance ($\sim 217$ pc, Maheswar et al. 2011)" (3.1 1.3mm continuum); "18^h16^m59.4973s\pm0.0002^s, -18^{\circ} 02\ensuremath{'} 30\ensuremath{''}.263\pm 0.001\ensuremath{''}" (Table 1)

## Data provenance

- ALMA projects: 2013.1.00783.S
- bands: Band 6, 1.3 mm continuum  
  > "1.3 mm continuum at ALMA band 6 and $^{12}$CO, $^{13}$CO, and C$^{18}$O 2-1 lines" (Summary)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 34 12-m antennas  
  > "In both observations 34 (12-m) antennas were used." (Observations)
- configurations: C34-6 (2014 Sep 1) and C34-2 (2015 Apr 14)  
  > "The first observation was made on September 1st, 2014 in C34-6 configuration" (Observations); "The second observation was carried out on April 14, 2015 in C34-2 configuration." (Observations)
- baselines: 14.1 m to 1091 m  
  > "Maximum baseline | 1091.0 m | 304.6 m" (Table 1)
- angular resolution: 0.31x0.23 arcsec continuum (robust 0.5 combined)  
  > "The synthesized beam size of our combined data with r=0.5 is 0$''$.31$\times$0$''$.23 (P.A.=79$^{\circ}.3$) in continuum emission." (Observations)
- max recoverable scale: 11.4 arcsec  
  > "putting a limit of a maximum recoverable scale of $11\ensuremath{''}.4$" (Observations)
- sensitivity: continuum ~0.04 mJy/beam; line ~4.0 mJy/beam per 0.096 km/s  
  > "$\rm \sim0.04~mJy~beam^{-1}$ and $\rm \sim4.0~mJy~beam^{-1}~[0.096~km/s]^{-1}$, respectively" (Observations)
- time on source: _not stated_
- observing dates: 2014-09-01 and 2015-04-14  
  > "Observing dates | Sept. 1, 2014 | April 14, 2015" (Table 1)
- pi or archival as stated: _not stated_
- Line: 12CO 2-1 (230.5380 GHz)
- Line: 13CO 2-1 (220.3987 GHz)
- Line: C18O 2-1 (219.56036 GHz)
- External data: Distance to L328-IRS ~217 pc  
  > "at its distance ($\sim 217$ pc, Maheswar et al. 2011)" (3.1 1.3mm continuum) [from Maheswar et al. 2011]
- External data: Dust temperature 16 K of envelope  
  > "at the dust temperature of 16 K from Lee et al. (2013)" (3.1 1.3mm continuum) [from Lee et al. (2013)]
- External data: Internal luminosity ~0.05 Lsun  
  > "its internal luminosity $\sim 0.05~{\rm\,L_\odot}$ (Lee et al. 2009)" (4.3 ALMA estimation of mass accretion rate) [from Lee et al. 2009]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Neptune  
  > "Flux calibrator | Neptune | Neptune" (Table 1)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: robust = 0.5 chosen after testing natural, uniform and long-baseline-only  
  > "the data with r=0.5 gave the most reasonable quality for our forthcoming analysis in terms of sensitivity and spatial resolution." (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: two configurations combined in visibility space  
  > "We combined the data from two configuration observations in visibility space and deconvolved the combined data" (Observations)
- smoothing: _not stated_
- final beam: 0.31x0.23 arcsec (PA 79.3 deg) continuum; 0.33x0.25 (PA 76.9) lines  
  > "0$''$.33$\times$0$''$.25(P.A.=76$^{\circ}$.9)" (Table 1)
- final rms: ~0.04 mJy/beam continuum  
  > "$\sim$0.04 mJy beam$^{-1}$" (Table 1)

### Inherited from earlier work

- Entrainment efficiency 0.25, Mdot_W/Mdot_acc=0.1, wind velocity 150 km/s  
  > "we adopted the same values for $f_{ent}$(=0.25), ${\dot M_{W} \over \dot M_{acc}}=0.1$, and the jet/wind velocity $\rm V_{W}\sim150~km~s^{-1}$ as those adopted by Lee et al. (2013)" (4.3 ALMA estimation of mass accretion rate) [from Lee et al. (2013)]

### Not stated but needed to reproduce (our reading)

- CASA version and whether the pipeline or manual calibration was used
- Self-calibration, if any
- Cell size, image size, clean threshold, masking and deconvolver
- Continuum-subtraction line-free channels
- Channel width and velocity resolution of the images used for PV and moment maps
- Exact PV cut width and Gaussian fit details
- Details of the toy model rendering and masking of the observed maps
- Outflow velocity and channel ranges, and the T_ex and tau derivation procedure
- Basis for the 5 sigma cut and background treatment in the outflow force

## Analysis recipe

1. **Measure continuum disk size, flux, and mass**: 2D Gaussian fit to the 1.3 mm continuum; mass from optically thin dust emission  
  > "Peak position of the continuum is measured from its 2D Gaussian fit" (3.1 1.3mm continuum)
   - parameter: kappa_1.3mm=0.014 cm2/g (beta=1.3); T_dust=16 K (30 K alternative)  
  > "$\rm \kappa_{1.3mm}=0.014~cm^{2}~g^{-1}$ with $\beta=1.3$" (3.1 1.3mm continuum)
   - assumption: Gas-to-dust ratio 100  
  > "A gas to dust mass ratio is assumed to be 100" (3.1 1.3mm continuum)
   - fitting: _not stated_
   - validation: Disk PA differs from beam PA by ~27 deg, so the elongation is not a beam effect  
  > "is not likely affected by the observed beam, but is instead a real feature" (3.1 1.3mm continuum)
2. **Derive disk rotation curve and dynamical mass**: PV diagram along the major axis; Gaussian fit to the spectrum at each position; subtract systemic velocity; compare with Keplerian curves  
  > "We fitted each spectrum with a Gaussian function to obtain the velocity at its peak intensity at each position." (4.1 Rotational kinematics)
   - parameter: Disk PA 106.5 deg; inclination 25.2 deg; systemic velocity 6.61 km/s  
  > "Our obtained systemic velocity is 6.61 $\rm km~s^{-1}$" (4.1 Rotational kinematics)
   - assumption: Circular disk; inclination from arcsin(b/a)  
  > "we assume that the disk is in circular shape when it is viewed face-on" (4.1 Rotational kinematics)
   - fitting: Keplerian curves for 0.05-0.4 Msun compared by eye; no formal sampler stated  
  > "theoretical Keplerian motions in the disk by the central point sources of 0.05 to 0.4 ${\rm\,M_\odot}$" (4.1 Rotational kinematics)
   - validation: Repeated with 13CO, giving similar results  
  > "We found very similar results seen in diagrams for C$^{18}$O line data in Figure 10" (4.1 Rotational kinematics)
3. **Constrain outflow inclination and opening angle**: 3D toy cavity model grid compared with observed blue/red CO maps via the sum of pixel-wise products  
  > "we multiplied intensities from the same pixels between each model and the observed data, and summed them." (4.2 Overall system)
   - parameter: Coarse grid of 49 models at 5 deg; fine grid of 256 models at 1 deg; opening angle 75-105 deg, inclination 50-80 deg  
  > "256 models in a finer interval of $1^{\circ}$" (4.2 Overall system)
   - assumption: Uniform emissivity, no radiative transfer, cavity thickness 0.45 arcsec  
  > "all pixels in charge of the outflow structures emit the same intensity, there is no radiative transfer effect in the model system" (4.2 Overall system)
   - fitting: _not stated_
   - validation: A 3-5 deg change reduces the sum by ~6%  
  > "will reduce $\sim 6\%$ of the sum value at the peak" (4.2 Overall system)
4. **Compute outflow force and mass accretion rate**: Pixel- and channel-wise CO column density (LTE), opacity-corrected using 13CO; momentum/dynamical-time outflow force; Mdot_acc from the outflow force  
  > "T_{12} (i,j) can be opacity-corrected from the following equation under the assumption that the 12CO and 13CO are at LTE with the same excitation temperature" (4.3 ALMA estimation of mass accretion rate)
   - parameter: X_CO=1e-4; [12CO]/[13CO]=62; mu_H2=2.8; 5 sigma cut; T_ex 9.9-38.2 K  
  > "the abundance ratio which is assumed to be 62 (Langer & Penzias 1993)" (4.3 ALMA estimation of mass accretion rate)
   - assumption: 13CO optically thin; outflow inclination 66 deg; T_ex=9.9 K where 13CO is undetected  
  > "we simply assume that CO 2-1 line would be optically thin and the excitation temperature would be as cold as $\sim 9.9$ K" (4.3 ALMA estimation of mass accretion rate)
   - fitting: _not stated_
   - validation: Using T_ex of 38.2 K instead of 9.9 K gives almost the same result; consistent with single-dish value rescaled to 66 deg  
  > "gives almost the same total outflow force and mass accretion rate as the results with the excitation temperature of 9.9 K" (4.3 ALMA estimation of mass accretion rate)
5. **Indirect central mass estimates**: Mass from accretion luminosity matching L_int, and from accreted mass over the dynamical time at constant rate  
  > "the total accreted mass would be $\sim 0.023~{\rm\,M_\odot}$ in this case" (4.3 ALMA estimation of mass accretion rate)
   - parameter: L_acc = G M Mdot/(2R); L_int ~0.05 Lsun; dynamical time ~2.8e4 yr; 10% outflow extraction  
  > "with an assumption of $10\%$ extraction of the accreted mass through the outflow" (4.3 ALMA estimation of mass accretion rate)
   - assumption: L_int is entirely from accretion; constant accretion rate  
  > "Valid only if $\dot M_{acc}$ is constant during dynamical time" (Table 2)
   - fitting: _not stated_
   - validation: Two independent assumptions give consistent masses; authors keep the identification tentative  
  > "Thus the identification of L328-IRS as a proto-brown dwarf must be considered tentative." (Summary)

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum deconvolved size | 0.40 x 0.17 arcsec (~87 x 37 AU) | ±0.01 arcsec | arcsec | 1 | 0\ensuremath{''}.40 ~(\pm  0\ensuremath{''}.01) \times 0\ensuremath{''}.17 ~(\pm 0\ensuremath{''}.01) |
| Continuum integrated flux density | 11.40 | 0.22 | mJy | 1 | $\rm 11.40~(\pm 0.22)$ mJy |
| Continuum mass (T=16 K) | ~0.01 | not stated | Msun | 1 | is about 0.01 $\rm M_\odot$ at the dust temperature of 16 K |
| Systemic velocity | 6.61 | not stated | km/s | 2 | Our obtained systemic velocity is 6.61 $\rm km~s^{-1}$ |
| Keplerian dynamical mass (C18O, 130-60 AU) | ~0.30 | not stated | Msun | 2 | the best fitted with the Keplerian motions in the disk by a stellar object of $\sim0.30 ~{\rm\,M_\odot}$ |
| Keplerian dynamical mass (13CO, 140-60 AU) | ~0.27 | not stated | Msun | 2 | by a central object of $\sim 0.27{\rm\,M_\odot}$ |
| Outflow inclination | 66 | not stated | deg | 3 | an opening angle of $92^{\circ}$ and an inclination angle of $66^{\circ}$ |
| Outflow opening angle | 92 | not stated | deg | 3 | an opening angle of $92^{\circ}$ |
| Mass accretion rate | ~8.9e-7 | not stated | Msun/yr | 4 | a total mass accretion rate is derived to be $\sim 8.9\times 10^{-7} {\rm\,M_\odot}~yr^{-1}$ |
| CO 2-1 optical depth range | 11-62.0 | not stated | dimensionless | 4 | Our derived optical depths for CO were between 11 and 62.0 |
| Accretion luminosity for 0.3 Msun | ~1.3 | not stated | Lsun | 5 | its accretion luminosity is estimated to be $\sim 1.3~{\rm\,L_\odot}$ |
| Mass from internal luminosity | ~0.012 | not stated | Msun | 5 | can be estimated to be $\sim 0.012~{\rm\,M_\odot}$ |
| Accreted mass over dynamical time | ~0.023 | not stated | Msun | 5 | the total accreted mass would be $\sim 0.023~{\rm\,M_\odot}$ |

## Qualitative findings

- Disk rotation is Keplerian only between ~130 and 60 AU; inside 60 AU velocities decrease, resembling solid rotation.  
  > "Its decreasing pattern within 60 AU is close to that of solid rotation" (4.1 Rotational kinematics)
- Inverse P Cygni CO profiles indicate infall across the envelope.  
  > "infalling motions of gaseous material traced in CO 2-1 are occurring nearly all over the envelope of L328-IRS" (4.2 Overall system)

## Claim tuples

- H: Can the central mass of L328-IRS be measured kinematically from the disk? | E: PV analysis of C18O and 13CO along the disk major axis with Keplerian comparison | R: Keplerian fit ~0.30 Msun only for 60-130 AU; inner region is non-Keplerian | F: A reliable dynamical mass cannot be determined | **partially**
- H: Does ALMA constrain the outflow inclination and the mass accretion rate better than single-dish data? | E: 3D toy-model grid fit of the CO outflow structures and an opacity-corrected outflow force | R: Inclination ~66 deg; Mdot ~8.9e-7 Msun/yr | F: Accretion rate is better determined and consistent with the single-dish value rescaled to 66 deg | **supported**
- H: Is L328-IRS substellar? | E: Mass from L_int and from the accreted mass over the dynamical time | R: ~0.012 and ~0.023 Msun | F: Suggests a substellar object, but the identification stays tentative | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: C18O chosen for disk kinematics; 13CO used for the opacity correction because C18O is detected only over the disk.  
  > "we used $\rm ^{13}CO$ 2-1 emission because $\rm ^{13}CO$ 2-1 is detected fairly well over the outflow area" (4.3 ALMA estimation of mass accretion rate)
- Alternative: Natural, uniform, and long-baseline-only weightings were tested; robust 0.5 was adopted.  
  > "We reduced our data with different robust weights 1) Natural, 2) Uniform, 3) long baseline data only" (Observations)
- How they decided it was enough: _not stated_
- Limitation (authors): The accretion rate depends on uncertain parameters (entrainment efficiency, mass-loss ratio, wind velocity) and on the assumption of a constant rate.  
  > "Our estimation of accretion rate can be affected by various uncertain parameters including the entrainment efficiency" (4.3 ALMA estimation of mass accretion rate)
- Limitation (authors): A stellar mass cannot be ruled out.  
  > "we can not completely rule out a possibility that L328-IRS can have a stellar mass, too" (4.3 ALMA estimation of mass accretion rate)
- Caveat (inferred, ours): The inclination from the continuum aspect ratio (25 deg) conflicts with the outflow inclination of 66 deg, which affects the Keplerian mass
- Caveat (inferred, ours): Toy model with uniform emissivity and no velocity information; no formal uncertainties
- Caveat (inferred, ours): Rotation curve is fitted by eye with no error bars
- Caveat (inferred, ours): Infall and outflow contamination of C18O and 13CO
- Caveat (inferred, ours): Envelope resolved out, which affects CO optical depth and outflow mass

## Reproducibility

- Data public (paper): Project code given; public status not explicitly stated  
  > "(with an ALMA project number of 2013.1.00783.S)" (Observations)
- Products in archive: _not stated_
- Missing: Calibration and imaging scripts and parameters
- Missing: Toy model code
- Missing: PV and rotation curve fitting details
- Data volume (inferred): ~50-100 GB raw for two Cycle 2 execution blocks
- Score (inferred): 3/5, The archive project is identified and the analysis equations are given, but imaging parameters, model code and fit details are missing.
- Rediscovery candidate: no, Several key analysis steps (toy model, rotation fit) are not specified well enough to reproduce.

## Links

- Method: Bontemps et al. 1996 (Outflow force and accretion rate formulation)
- Method: Dunham et al. 2014 (CO column density method)
- Companion: Lee et al. (2013) (Previous single-dish study identifying L328-IRS as a proto-BD candidate)
- Related: Spitzer VeLLO survey

## Checks

```json
{
 "quotes": 74,
 "quotes_ok": 74,
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
  "facts": 77,
  "stated": 49,
  "rate": 0.636
 },
 "evidence_ok": true
}
```
