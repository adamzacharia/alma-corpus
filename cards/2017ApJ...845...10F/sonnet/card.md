# Strongly Misaligned Triple System in SR 24 Revealed by ALMA

`2017ApJ...845...10F` | The Astrophysical Journal 2017 | first author: Fernández-López, M. | arXiv: 1707.01128 | DOI: 10.3847/1538-4357/aa7d51

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks, star_formation
- Question: Are the disks of the young triple system SR24 misaligned, and what are their masses, kinematics and the extended gas structures around them?  
  > "we present ALMA millimeter observations toward the triple system SR24 showing that disks in this system are strongly misaligned and possibly counter-rotating in projection." (Introduction)
- Target **SR24 (SR24S, SR24N)**: coordinates SR24S 16:26:58.504 -24:45:37.21; SR24N 16:26:58.434 -24:45:32.24 (J2000)  
  > "The phase center was at $(\alpha,\delta)$J2000.0=($16^h26^m58.506s$,$-24\ensuremath{^\circ}45\ensuremath{'}35.87\ensuremath{''}$)" (Observations); "(120 AU for the adopted distance)" (3.3 Simple modeling of the SR24S disk kinematics); z/distance 120 pc (d=0.12 kpc)  
  > "The phase center was at $(\alpha,\delta)$J2000.0=($16^h26^m58.506s$,$-24\ensuremath{^\circ}45\ensuremath{'}35.87\ensuremath{''}$)" (Observations); "(120 AU for the adopted distance)" (3.3 Simple modeling of the SR24S disk kinematics); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.000912.S, 2013.1.00498.S
- bands: 1.3 mm (227 GHz) continuum, CO (2-1) lines  
  > "inferred from the 1.3 mm (227 GHz) continuum and several CO isotopologues" (2.1 ALMA archive observations)
- frequencies and spectral setup: Continuum project: four windows at 219.550, 220.383, 234.507, 232.987 GHz; 12CO project: window at 230.714 GHz, 469 MHz, 1920 channels, 244 kHz resolution  
  > "The four windows were centered at 219.550 GHz, 220.383 GHz, 234.507 GHz and 232.987 GHz." (2.1 ALMA archive observations); "This spectral window has 1920 channels, which provides a spectral resolution of 244 kHz" (2.1 ALMA archive observations)
- continuum bandwidth: 7.5 GHz  
  > "The final 7.5 GHz continuum image was obtained using natural weighting." (2.1 ALMA archive observations)
- arrays: _not stated_
- configurations: _not stated_
- baselines: up to 2270 m (continuum/C18O, 34 antennas); 15.1 m to 1600 m (12CO, 44 antennas)  
  > "ALMA had 34 operative antennas with baselines ranging up to 2270 m" (2.1 ALMA archive observations); "with 946 baselines ranging from 15.1 m to 1600 m" (2.1 ALMA archive observations)
- angular resolution: continuum 0.18x0.12 arcsec; C18O 0.21x0.16; 12CO 0.60x0.54 (tapered) and 0.25x0.21 (natural)  
  > "Its synthesized beam is $0.18\ensuremath{''}\times0.12\ensuremath{''}$ with a P.A.$=71.5\ensuremath{^\circ}$" (2.1 ALMA archive observations)
- max recoverable scale: _not stated_
- sensitivity: continuum rms 44 uJy/beam; C18O 1.2 mJy/beam per 1.35 km/s; 12CO 4.6 (taper) and 5.2 mJy/beam per 0.6 km/s  
  > "its rms noise level is 44 $\mu$Jy beam$^{-1}$" (2.1 ALMA archive observations)
- time on source: 23.3 min (continuum/C18O); 12.6 min (12CO)  
  > "The time on source was 23.3 minutes." (2.1 ALMA archive observations); "for 12.6 minutes" (2.1 ALMA archive observations)
- observing dates: 2015 Sept 26 (C18O/continuum); 2015 July 21 (12CO)  
  > "The $^{12}$CO (2-1) dataset was obtained on July 21st, 2015 (project 2013.1.00498.S)." (2.1 ALMA archive observations)
- pi or archival as stated: archival  
  > "By using archival ALMA observations we report the detection at 1.3 mm" (Summary and Conclusions)
- Line: 12CO 2-1 (230.538 GHz)
- Line: C18O 2-1 (not stated)
- Other facility **SMA**: archival 12CO(2-1) data sensitive to extended emission; used for masses of reservoir and bridge  
  > "We estimate the mass of the northern gas reservoir and the gas bridge between the disks using the $^{12}$CO(2-1) SMA emission" (3.4 Molecular extended emission)
- Other facility **HST ACS**: archival 6000 A image overlay  
  > "overlapped with an archival HST ACS $6000$Å image" (3.1 Continuum emission from the disks)
- External data: Dust opacity 1.1 cm2/g at 1.3 mm  
  > "a dust opacity of 1.1 cm$^2$ g$^{-1}$ at 1.3 mm appropriate for dust with thin ice mantles" (3.1 Continuum emission from the disks) [from (cite: 1994Ossenkopf)]
- External data: Opacity index beta=0.4  
  > "an opacity spectral index with an exponent $\beta=0.4$ for both sources" (3.1 Continuum emission from the disks) [from (cite: 2009Isella; 2010Ricci; 2014Pinilla)]
- External data: Binary SR24Nb/Nc orbit and mass of close binary  
  > "is in good agreement with the total mass of the close binary system" (3.2 12CO Molecular emission from the disks) [from (cite: 2006Correia)]
- Simulation/model as data: Toy kinematic models (Cases I-III) of rotating/accreting disks with different inclinations and infall  
  > "we show sketches for two rotating and accreting disks with inclinations separated by $180\ensuremath{^\circ}$ and a third rotating disk with no accretion" (4.1 Geometry of the disks)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Pallas (continuum/C18O); Titan (12CO)  
  > "Observations of the asteroid Pallas were used to set the absolute scale for the flux density calibration." (2.1 ALMA archive observations); "Saturn’s moon Titan was used as the absolute flux calibrator" (2.1 ALMA archive observations)
- flux scale uncertainty: SMA: 15-20%  
  > "The uncertainty in the flux scale is estimated to be between 15% and 20%" (2.2 SMA archive observations)
- self calibration: continuum self-calibrated and cleaned three times; C18O cube made after applying selfcal solution  
  > "We self-calibrated and cleaned the final continuum image three times and applied a mask surrounding the two main sources detected in SR24." (2.1 ALMA archive observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting for continuum, C18O, 12CO second cube; SMA robust=2  
  > "The final 7.5 GHz continuum image was obtained using natural weighting." (2.1 ALMA archive observations); "We used the ROBUST parameter of CLEAN set to 2" (2.2 SMA archive observations)
- uv taper: uv-taper used for one 12CO cube (taper value not given)  
  > "The first velocity cube was obtained after applying a uv-taper to stress the extended $^{12}$CO emission." (2.1 ALMA archive observations)
- cell size: _not stated_
- image size: _not stated_
- masking: mask around the two main continuum sources  
  > "applied a mask surrounding the two main sources detected in SR24" (2.1 ALMA archive observations)
- multiscale scales: _not stated_
- continuum subtraction: line channels removed before adding line-free windows to continuum  
  > "most of which where line-free and were hence added to the continuum after removing the line channels" (2.1 ALMA archive observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: continuum 0.18x0.12 arcsec PA 71.5; C18O 0.21x0.16 PA 76.6  
  > "The synthesized beam of the C$^{18}$O data is $0.21\ensuremath{''}\times0.16\ensuremath{''}$ with a P.A.$=76.6\ensuremath{^\circ}$" (2.1 ALMA archive observations)
- final rms: 44 uJy/beam continuum; 1.2 mJy/beam C18O  
  > "a rms noise level of 1.2 mJy beam$^{-1}$ per 1.35 km s$^{-1}$ channel" (2.1 ALMA archive observations)

### Inherited from earlier work

- Surface density gamma fixed to 0.8  
  > "$\gamma$ is the power law index that we fixed to 0.8 following (cite: 2010Andrews)" (3.3 Simple modeling of the SR24S disk kinematics) [from (cite: 2010Andrews)]
- Optimization via AGA method  
  > "We used an optimization algorithm based on the AGA method developed by (cite: 2009Canto)" (3.3 Simple modeling of the SR24S disk kinematics) [from (cite: 2009Canto)]
- Misalignment angle formula  
  > "We follow the expression given in (cite: 2014Jensen)" (Footnote 8) [from (cite: 2014Jensen)]

### Not stated but needed to reproduce (our reading)

- CASA version and whether the pipeline or manual calibration was used
- self-calibration solution intervals and reference
- uv-taper value and clean parameters (threshold, niter, cell, image size)
- line-free channels and continuum subtraction method
- AGA code and parameter bounds/priors
- how the 12CO disk velocity ranges and 2D Gaussian fits were done
- how errors on inclination and PA were propagated
- source of the 120 pc distance

## Analysis recipe

1. **Image continuum and measure disk properties**: Self-calibrated natural-weighted 1.3 mm image; source flux, size, PA from deconvolved ellipse; inclination = arccos(Rmin/Rmaj)  
  > "Estimated from the major and minor axis lengths as the $\arccos(R_{min}/R_{maj})$." (Table 1)
   - software: CASA, MIRIAD, GILDAS
   - fitting: _not stated_
   - validation: _not stated_
2. **Estimate disk dust masses**: Optically thin isothermal dust emission  
  > "Assuming optically thin isothermal dust emission, a gas-to-dust ratio of 100" (3.1 Continuum emission from the disks)
   - parameter: kappa=1.1 cm2/g at 1.3 mm, beta=0.4, T_dust=30 K  
  > "a dust temperature of 30 K" (3.1 Continuum emission from the disks)
   - assumption: gas-to-dust ratio 100  
  > "a gas-to-dust ratio of 100" (3.1 Continuum emission from the disks)
   - fitting: _not stated_
   - validation: compared with previous mass estimates for SR24S  
  > "in good agreement with previous estimates" (3.1 Continuum emission from the disks)
3. **Characterize 12CO disk kinematics and SR24N dynamical mass**: 2D Gaussian fits to moment 0, PV diagrams with Keplerian curves, M=0.00121*(dv/2)^2*r  
  > "$(M/M_{\ensuremath{\odot}})=0.00121\times((\Delta v/km~s^{-1})/2)^2\times(r/AU)$" (3.2 12CO Molecular emission from the disks)
   - software: CASA, KARMA, MIRIAD
   - fitting: 2D Gaussian fit  
  > "This absorption is possibly affecting the results of our 2D-Gaussian fit, which would explain the different inclination obtained" (Results, 12CO Molecular emission from the disks)
   - validation: Keplerian curves overlaid on PV diagram  
  > "we overlapped three Keplerian rotation curves produced with central masses ranging between 0.1 $M_{\ensuremath{\odot}}$ and 1 $M_{\ensuremath{\odot}}$" (3.2 12CO Molecular emission from the disks)
4. **Fit SR24S C18O velocity cube with kinematic model**: Thin rotating, accreting disk with tapered power-law surface density, r^-0.5 rotation and infall, no radiative transfer; 9 free parameters; M=v_rot^2 r/G  
  > "Our model of the velocity cube has 9 free parameters" (3.3 Simple modeling of the SR24S disk kinematics)
   - software: MIRIAD (velmodel, velimage)
   - parameter: gamma=0.8; fiducial radius 1 arcsec (120 AU)  
  > "at a fiducial radius of $1\ensuremath{''}$ (120 AU for the adopted distance)" (3.3 Simple modeling of the SR24S disk kinematics)
   - assumption: distance 120 pc  
  > "the distance is d=0.12 kpc" (Results, Molecular extended emission)
   - fitting: AGA-based optimization, run 100 times to get standard deviations  
  > "ran it a 100 times in order to extract a standard deviation for the averaged parameters" (3.3 Simple modeling of the SR24S disk kinematics)
   - validation: visual agreement with cube and PV diagram  
  > "Figure [5](#Ffit) shows the good agreement between the simple model and the C$^{18}$O (2-1) observed velocity cube" (3.3 Simple modeling of the SR24S disk kinematics)
5. **Determine tilt/sense of rotation and misalignment angle**: PV cuts perpendicular to major axis compared with synthetic infall models; angle via cosΔ=cos i1 cos i2+sin i1 sin i2 cos(PA1-PA2)  
  > "$\cos{\Delta}=\cos{i_1}\cdot\cos{i_2}+\sin{i_1}\cdot\sin{i_2}\cdot\cos{(PA_1-PA_2)}$" (Footnote 8)
   - software: MIRIAD
   - assumption: SR24N disk rotates in same sense as the close binary; infall rather than outflow  
  > "we assume that the sense of the disk rotation matches that of the close binary system SR24Nb and SR24Nc" (4.1 Geometry of the disks)
   - fitting: _not stated_
   - validation: consistency with IR spiral arm and brightness asymmetry  
  > "The curvature of the spiral arm would indicate that the disk is rotating counterclockwise (as seen in projection), which implies that east is its near side." (Discussion, Geometry of the disks)
6. **Mass of extended gas from SMA 12CO**: LTE optically thin mass formula with Tex=30 K, X_CO/X_H2=1e-4, d=0.12 kpc  
  > "we adopt an excitation temperature $T_{ex}=30$ K" (3.4 Molecular extended emission)
   - software: MIRIAD
   - assumption: LTE, optically thin  
  > "assuming that the gas is in local thermodynamic equilibrium and its emission is optically thin" (3.4 Molecular extended emission)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : calibration, imaging, analysis  
  > "The data were calibrated, imaged and analyzed using CASA" (2.1 ALMA archive observations)
- **KARMA** : imaging/analysis  
  > "The data were calibrated, imaged and analyzed using CASA" (2.1 ALMA archive observations)
- **MIRIAD** : analysis, velmodel/velimage kinematic model, SMA data  
  > "We implemented the kinematics of the rotating and accreting disk using the Miriad tasks *velmodel* and *velimage*" (3.3 Simple modeling of the SR24S disk kinematics)
- **GILDAS** : data analysis  
  > "MIRIAD (cite: 1995Sault) and GILDAS[^1] packages" (2.1 ALMA archive observations)
- **MIR (IDL)** : SMA data reduction  
  > "The data were analyzed in the standard manner using the IDL-based MIR software package" (2.2 SMA archive observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| SR24S 1.3 mm flux density | 211 | 4 | mJy | 1 | 211$\pm$4 |
| SR24N 1.3 mm flux density | 0.34 | 0.07 | mJy | 1 | 0.34$\pm$0.07 |
| SR24S disk mass | 0.025 | 0.007 | Msun | 2 | for SR24S we obtain a mass of 0.025$\pm0.007$ $M_{\ensuremath{\odot}}$ |
| SR24N disk mass | 13 | 7 | Mearth | 2 | $4\times10^{-5}$ $M_{\ensuremath{\odot}}$ or 13$\pm7$ $M_{\ensuremath{\oplus}}$ |
| SR24S C18O dynamical mass | 1.5 | 0.5 | Msun | 4 | of 1.5$\pm$0.5 $M_{\ensuremath{\odot}}$ |
| SR24S fitted inclination (C18O) | 46 | 8 | deg | 4 | $i$                      / $46\ensuremath{^\circ}$  / $8\ensuremath{^\circ}$ / |
| SR24S fitted characteristic radius | 1.3 | 0.2 | arcsec | 4 | $r_c$                    / $1.3\ensuremath{''}$     / $0.2\ensuremath{''}$   / |
| SR24N dynamical mass | 0.8 (order-zero; abstract/summary quote 1.1) | not stated | Msun | 3 | The resulting mass, 0.8 $M_{\ensuremath{\odot}}$, is in good agreement |
| Angle between disk angular momentum vectors | 108 | 25 | deg | 5 | we derive an angle between the angular momentum vectors of the two disks[^8] of $108\ensuremath{^\circ}\pm25\ensuremath{^\circ}$ |
| Northern reservoir SMA 12CO flux | 11.3 | 0.3 | Jy km/s | 6 | Northern reservoir / 11.3$\pm$0.3 / 16.5 / 13 |

## Qualitative findings

- SR24N continuum detected for the first time at 1.3 mm; SR24S shows ring morphology  
  > "here we report for the first time the detection of SR24N in this wavelength domain" (3.1 Continuum emission from the disks)
- Three extended 12CO structures: northern reservoir, bridge, southern streamer  
  > "There are three main features that we point out" (3.4 Molecular extended emission)

## Claim tuples

- H: Are the SR24N and SR24S disks misaligned and counter-rotating? | E: Continuum and 12CO geometry, C18O kinematic model, PV asymmetry with infall models | R: Angle between angular momentum vectors 108±25 deg | F: Disks strongly misaligned and possibly rotate in opposite directions in projection | **supported**
- H: Is SR24N disk detected in continuum and what is its mass? | E: Optically thin dust mass from 1.3 mm flux | R: 7 sigma detection, mass ~13 Mearth | F: SR24N hosts a low-mass dust disk | **supported**
- H: What extended gas surrounds SR24? | E: Compare ALMA and SMA 12CO cubes | R: Bridge, northern reservoir, southern streamer with masses ~1e-7 to 1e-6 Msun | F: Northern reservoir may be key to origin of misalignment | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: C18O chosen since it is more optically thin and less affected by cloud absorption  
  > "This is the reason why the C$^{18}$O (2-1) line is the best molecular proxy available to study the kinematics of the SR24S disk." (3.3 Simple modeling of the SR24S disk kinematics)
- Alternative: If SR24N rotated oppositely, misalignment would be 66 deg  
  > "the disk’s angular momentum vectors would be $66\ensuremath{^\circ}$ away from each other" (4.1 Geometry of the disks)
- How they decided it was enough: _not stated_
- Limitation (authors): SR24N analysis limited by low S/N and cloud absorption in 12CO  
  > "the lower signal-to-noise ratio and the foreground cloud absorption of the $^{12}$CO data prevent a similar analysis" (4.1 Geometry of the disks)
- Caveat (inferred, ours): 12CO inclination (70 deg) disagrees with continuum (44 deg) due to absorption
- Caveat (inferred, ours): Sense of SR24N rotation assumed from binary orbit
- Caveat (inferred, ours): Toy model lacks radiative transfer; infall sign relies on assumption
- Caveat (inferred, ours): Mass inconsistency: SR24N 4e-5 Msun vs Mearth in abstract; 1.1 vs 0.8 Msun

## Reproducibility

- Data public (paper): archival ALMA and SMA data  
  > "By using archival ALMA observations we report the detection at 1.3 mm" (Summary and Conclusions)
- Products in archive: _not stated_
- Missing: CASA version and imaging parameters
- Missing: AGA fitting code and settings
- Missing: 12CO velocity range specifics
- Data volume (inferred): ~10-30 GB for two ALMA Cycle 1 datasets
- Score (inferred): 3/5, Public data and a clear simple recipe, but clean/selfcal parameters and fitting code details are missing.
- Rediscovery candidate: yes, Public data, numeric results (fluxes, masses, fitted parameters), moderately complete recipe.

## Links

- Method: (cite: 2009Canto) (AGA optimization algorithm)
- Method: (cite: 2014Jensen) (misalignment angle expression)
- Companion: (cite: 2017Pinilla) (other analysis of SR24S ALMA data)

## Checks

```json
{
 "quotes": 84,
 "quotes_ok": 84,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2013.1.000912.S"
 ],
 "obscore_codes_not_in_card": [
  "2013.1.00091.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 85,
  "stated": 59,
  "rate": 0.694
 },
 "evidence_ok": true
}
```
