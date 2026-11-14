# The HH30 edge-on T Tauri star. A rotating and precessing monopolar outflow scrutinized by ALMA

`2018A&A...618A.120L` | Astronomy and Astrophysics 2018 | first author: Louvet, F. | arXiv: 1808.03285 | DOI: 10.1051/0004-6361/201731733

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, star_formation
- Question: What is the origin of the small-scale molecular CO outflow of the edge-on T Tauri star HH30 (disk wind vs entrainment), and how is it linked to the disk and the binary/wiggling jet?  
  > "We aim to clarify the origin of the small-scale molecular outflow of HH30 and its link and impact on the accretion disk." (abstract)
- Target **HH30**: coordinates 04:31:37 +18:12:24 (J2000, phase centre)  
  > "at the phase centre $\alpha$(J2000) = 04:31:37 and $\delta$(J2000) =18:12:24" (2 Observations and data reduction); "located in the dark molecular cloud L1551 at a distance of $\sim$140 pc (cite: kenyon94) in Taurus" (Introduction); z/distance ~140 pc  
  > "at the phase centre $\alpha$(J2000) = 04:31:37 and $\delta$(J2000) =18:12:24" (2 Observations and data reduction); "located in the dark molecular cloud L1551 at a distance of $\sim$140 pc (cite: kenyon94) in Taurus" (Introduction); distance from Kenyon et al. 1994 (cite: kenyon94)  
  > "at the phase centre $\alpha$(J2000) = 04:31:37 and $\delta$(J2000) =18:12:24" (2 Observations and data reduction); "located in the dark molecular cloud L1551 at a distance of $\sim$140 pc (cite: kenyon94) in Taurus" (Introduction)

## Data provenance

- ALMA projects: _none stated_
- bands: Band 6 (211-275 GHz)  
  > "were observed using the Band 6 of ALMA (211-275GHz)" (2 Observations and data reduction)
- frequencies and spectral setup: Three 117.2 MHz line windows (960 channels) at 219.563, 220.379, 230.546 GHz (C18O, 13CO, 12CO); two 2 GHz continuum windows at 217.044 and 234.010 GHz  
  > "Two additional spectral windows of 2 GHz bandwidth in 128 channels centred at 217.044 GHz and 234.010 GHz were dedicated to the detection of the continuum emission" (2 Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: Cycle 2 semi-extended configuration  
  > "The data were taken using the cycle 2 semi-extended configuration of ALMA with baselines ranging from 13 m to 1570 m." (2 Observations and data reduction)
- baselines: 13 m to 1570 m  
  > "with baselines ranging from 13 m to 1570 m" (2 Observations and data reduction)
- angular resolution: ~0.26" x 0.19", PA ~29 deg  
  > "the synthesized beam has in average a size of 0.26$^{\prime\prime}$ $\times$0.19$^{\prime\prime}$ at a position angle (PA) of $\simeq$29$^\circ$" (2 Observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: Continuum rms 21.74 uJy/beam; 12CO 1.9 mJy/beam and 13CO 2.15 mJy/beam per 0.3 km/s channel  
  > "The $^{12}$CO(2-1) and $^{13}$CO(2-1) emission lines display a rms noise level of 1.9 mJy/beam and 2.15 mJy/beam per channel, respectively." (2 Observations and data reduction)
- time on source: Each track ~40 min  
  > "Each track lasted $\sim$40 minutes." (2 Observations and data reduction)
- observing dates: July 19 and 21, 2015  
  > "Two tracks were performed on July 19, 2015 and one on July 21, 2015." (2 Observations and data reduction)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (230.538 GHz)
- Line: 13CO J=2-1 (220.398 GHz)
- External data: Continuum spectral index S ~ nu^2.2 for disk, used to merge continuum bands  
  > "Assuming that the continuum spectrum is accurately described by $S(\nu) \propto \nu^{2.2}$ in the disk, as derived by P06" (2 Observations and data reduction) [from Pety et al. 2006 (cite: pety06)]
- External data: Enclosed stellar mass 0.45 Msun used for Keplerian/launching radius estimates  
  > "Keplerian rotation around an enclosed mass of 0.45 $\pm$ 0.04 M$_\odot$" (Introduction) [from Pety et al. 2006 (cite: pety06)]
- External data: Orbital binary solution of the jet (a=18 au, precession-equivalent parameters)  
  > "showed that the kinematics and positions of the knots in the HH30 atomic jet and counter-jet can be reproduced by the orbital motion of the jet source in a binary system with separation of $a = 18.0 \pm 0.6$ au" (5.1.3) [from Estalella et al. 2012 (cite: estalella12)]

## Processing

### Calibration

- pipeline or manual: Reduced with CASA; one track discarded for phase drifts; continuum windows used to correct phase centre and reproject cubes before merging  
  > "One of the tracks from July 19, 2015 (uid\_\_\_A002_Xa5df2c_X9030) was put aside due to irregular phase drifts over short (minutes) timescales." (2 Observations and data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: ~10%  
  > "we estimate the absolute flux calibration to be accurate within $\sim$10%" (2 Observations and data reduction)
- self calibration: _not stated_

### Imaging

- task: Cleaning method HOGBOM of GILDAS  
  > "Imaging was carried out using the cleaning method HOGBOM of the GILDAS[^1] package." (2 Observations and data reduction)
- deconvolver: _not stated_
- weighting robust: ROBUST weighting, parameter 0.56  
  > "With a ROBUST weighting and a parameter of 0.56[^2]" (2 Observations and data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: 234.010 GHz continuum subtracted from 12CO, 217.044 GHz continuum from 13CO  
  > "We used the 234.010 GHz continuum emission to subtract from the $^{12}$CO(2-1) emission and the 217.044 GHz continuum emission to subtract from the $^{13}$CO(2-1) emission." (2 Observations and data reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Velocity resolution degraded from 0.16/0.17 to 0.3 km/s  
  > "which we degraded to 0.3 km s$^{-1}$ to detect weak emission" (2 Observations and data reduction)
- final beam: _not stated_
- final rms: Continuum 21.74 uJy/beam  
  > "has a root mean square (rms) noise level of 21.74 $\mu$Jy/beam" (2 Observations and data reduction)

### Inherited from earlier work

- Pety et al. 2006 conical flow geometry/velocity and disk results as comparison baseline  
  > "Our ALMA observations show global morphological and kinematic properties similar to the PdBI observations of P06." (4.3) [from Pety et al. 2006 (cite: pety06)]
- Ring-fitting procedure of transverse pv diagrams, modified to allow wiggling  
  > "This procedure is very similar to that recently used by (cite: hirota17) except that we allow for possible wiggling of the flow axis." (4.3) [from Hirota et al. 2017 (cite: hirota17)]

### Not stated but needed to reproduce (our reading)

- Name of the phase/bandpass/flux calibrator quasars (blank in text)
- CASA version
- Pipeline or manual calibration details and self-calibration
- Cleaning mask, threshold, cell and image size in GILDAS
- Exact spectral channels used for continuum
- Details of rectangle for disk subtraction
- ALMA project code (not printed in paper)

## Analysis recipe

1. **Calibrate and image data**: CASA calibration, merge two tracks, GILDAS Hogbom cleaning with robust weighting  
  > "Imaging was carried out using the cleaning method HOGBOM of the GILDAS[^1] package." (2 Observations and data reduction)
   - software: CASA, GILDAS
   - parameter: robust 0.56; 0.3 km/s channels  
  > "With a ROBUST weighting and a parameter of 0.56[^2]" (2 Observations and data reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure continuum disk and 13CO Vlsr**: Intensity cuts across/along disk; Gaussian fits to 13CO spectrum wings for Vlsr  
  > "To determine the $V_{\rm lsr}$ of , we fit a single Gaussian component to the high-velocity wings of the $^{13}$ CO profile" (3.2)
   - assumption: Thin equatorial dust layer for inclination lower limit; distance 140 pc  
  > "Assuming that the continuum emission comes from a thin layer of dust in the equatorial plane of the disk" (3.1)
   - fitting: _not stated_
   - validation: _not stated_
3. **Subtract disk emission from 12CO**: Pixel-by-pixel subtraction of the mirrored southern emission from northern emission in each channel, assuming disk symmetry  
  > "The emission at a given vertical offset $-y$ is subtracted from its symmetric position at a positive $+y$ offset." (4.1)
   - assumption: Southern 12CO is disk only; disk symmetric about mid-plane as in 13CO  
  > "we assume that the $^{12}$CO emission arising from the bottom hemisphere originates from the disk alone" (4.1)
   - fitting: _not stated_
   - validation: Compared with 13CO symmetry and 12CO following 13CO in south  
  > "which clearly shows that the $^{12}$CO emission closely follows the $^{13}$CO emission in the south-western hemisphere" (4.1)
4. **Derive CO cavity mass**: Optically thin upper-level column density, Boltzmann population with single Tex, converted to H2 mass  
  > "Making the assumption that the $^{12}$CO emission is governed by a single excitation temperature T$_{\rm ex}$, the population of rotational levels of CO follows a Boltzmann distribution" (4.2)
   - parameter: Tex = 30 K lower limit; mean integral Tmb dV 38.7 K km/s  
  > "Now, using $T_{\rm ex}$ = 30 K as lower limit for the excitation temperature" (4.2)
   - assumption: CO abundance 1e-4, mu=1.4, d=140 pc  
  > "where $\mu$=1.4 is the mean gas weight per H$_2$ molecule, including 10% of helium" (4.2)
   - fitting: _not stated_
   - validation: Compared to P06 estimate of 2e-5 Msun  
  > "This value compares well with the estimation of 2$\times 10^{-5}$ M$_\odot$ by P06" (4.2)
5. **Fit ring model to transverse pv diagrams**: Gaussian fits of spectra at each transverse offset trace an ellipse, fitted with MPFITELLIPSE and converted to ring parameters (R, x_offset, Vz, Vr, Vphi); velocities 5-10 km/s excluded; errors doubled  
  > "An ellipse is then fitted to the trace using the IDL MPFITELLIPSE procedure." (4.3)
   - software: IDL MPFITELLIPSE
   - parameter: pv diagrams every 0.15" from z=0.1" to 1.75"  
  > "The fit is performed to each transverse pv diagram constructed every 0.15$^{\prime\prime}$ along the flow axis from z=0.1$^{\prime\prime}$ to z=1.75$^{\prime\prime}$." (4.4)
   - assumption: Narrow circular ring at each z; V0=0 (no orbital motion) for inclination  
  > "we assume that the $^{12}$CO emission arises from a narrow circular ring of gas" (4.3)
   - fitting: Least-squares ellipse fit; 1000 Monte Carlo realizations with Gaussian parameter errors give 1 sigma on ring parameters  
  > "We then compute 1000 sets of ellipse parameters by randomly drawing a realization for each parameter" (4.3)
   - validation: Reduced chi2 0.6-2.3 (4 at z=0.1")  
  > "Reduced $\chi^2$ range between 0.6 and 2.3 except at the first position" (4.4)
6. **Derive kinematics, inclination wiggle, angular momentum, launching radii and compare with wind/binary models**: Use Vr sin i/Vcent=tan(theta)tan(i) for inclination; Vphi sin i and R for specific angular momentum; Blandford & Payne relations and Keplerian/photoevaporation scalings for launching radius; compare to orbital and precession solutions  
  > "the ratio of the projected velocity components $\frac{V_r \times \sin{\rm i}}{Vcent}$= $\tan{\theta} \times \rm \tan{\rm i}$" (4.4)
   - assumption: Steady wind, M_star=0.45 Msun, gas flows along conical surface  
  > "for M$_{\rm star}$ = 0.45 M$_{\odot}$" (5.1.1)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Data reduction/calibration  
  > "The data were reduced using the common astronomy software application (cite: mcmullin06)." (2 Observations and data reduction)
- **GILDAS** : Imaging with Hogbom cleaning  
  > "Imaging was carried out using the cleaning method HOGBOM of the GILDAS[^1] package." (2 Observations and data reduction)
- **IDL MPFITELLIPSE** : Ellipse fitting to pv traces  
  > "An ellipse is then fitted to the trace using the IDL MPFITELLIPSE procedure." (4.3)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum disk axis PA | 31.2 | 0.1 | deg | 2 | The disk axis has a PA of $31.2^\circ \pm0.1$. |
| 1.33 mm continuum flux density | 22.30 | 0.05 | mJy | 2 | The resulting flux density of 22.30$\pm$0.05 mJy at 1.33 mm |
| Disk inclination lower limit | 84.8 | not stated | deg | 2 | provides a lower limit to the disk inclination of $i > 84.8^{\circ}$ |
| Vlsr | 6.9 | 0.1 | km/s | 2 | We derive a central velocity of $V_{\rm lsr} = 6.9$ $\pm$ 0.1 km s$^{-1}$ in $^{13}$CO |
| CO cavity mass lower limit | 1.7e-5 | not stated | Msun | 4 | = 1.7\times 10^{-5} \rm M_\odot |
| Cone semi-opening angle | 35 | 0.7 | deg | 5 | The variation of radius is fully consistent with a cone of semi-opening angle 35$^{\circ}$ $\pm$ 0.7$^{\circ}$. |
| Mean poloidal velocity | 9.3 | 0.7 | km/s | 6 | = 9.3 $\pm$ 0.7 km s$^{-1}$ |
| Specific angular momentum | 38 | 15 | au km/s | 6 | We derive an average specific angular momentum of 38 $\pm$ 15 au km s$^{-1}$ |
| CO mass flux lower limit | 9e-8 | not stated | Msun/yr | 6 | we confirm the large minimum mass flux of 9$\times 10^{-8}$ M$_\odot$ yr$^{-1}$ for the CO wind |
| Magnetic lever arm | 1.6 | not stated | dimensionless | 6 | we infer a launching radius of $r_0=$0.5-2.5 au and $\lambda$=1.6 |

## Qualitative findings

- CO outflow is monopolar to the north-east, a hollow cone, with an inner shell at z>2" and tentative on-axis knot  
  > "we detect signatures of an inner knot close to the source (z $\simeq$ 0.25$^{\prime\prime}$) and of an inner shell at large distances (z $>$ 2$^{\prime\prime}$)" (Conclusions)

## Claim tuples

- H: Does the CO cavity trace a slow disk wind? | E: Ring fits to transverse pv diagrams of disk-subtracted 12CO | R: Conical flow 35 deg, constant Vp 9.3 km/s, rotation in disk sense, j=38 au km/s | F: Compatible with photoevaporative or MHD disk wind with launching radii 0.5-7 au | **supported**
- H: Is the 18 au binary orbital scenario consistent with CO wiggling? | E: Compare predicted orbital and precession wiggles with measured centroid velocities and positions | R: Orbital solution predicts 1.5 km/s variations, not observed; precession solution matches | F: Orbital scenario ruled out (if disk wind); circumbinary-disk precession with close binary favoured | **supported**
- H: Does the continuum disk have an inner hole? | E: Intensity cut along the disk | R: Constant flux within 3 sigma out to 75 au | F: No inner hole, contradicting Guilloteau et al. 2008 | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Entrainment by wide-angle wind: constant Vr inconsistent with homologous expansion; stationary cavity from bow shocks remains possible  
  > "is not consistent with the homologous expansion law $\overrightarrow{V} \propto \overrightarrow{Z}$ predicted by (cite: lishu96)" (5.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Launching-radius inferences rely on a steady-state assumption; ACA data would be needed to rule out an envelope  
  > "Although ACA observations would be required to image this component fully and definitely rule out an envelope around HH30" (5.2)
- Caveat (inferred, ours): Disk-subtraction assumes perfect north-south disk symmetry in 12CO
- Caveat (inferred, ours): Excitation temperature of 30 K is only a lower limit, so mass and mass flux are lower limits
- Caveat (inferred, ours): Wiggle amplitude is near noise (~1 au offsets)
- Caveat (inferred, ours): Binary constraints are conditional on a steady disk-wind origin

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Project code and calibrator names
- Missing: CASA version and calibration scripts
- Missing: GILDAS clean parameters (masks, thresholds)
- Missing: Custom ring-fitting/pv extraction scripts
- Data volume (inferred): ~50-100 GB raw for 2 tracks (cycle 2 Band 6)
- Score (inferred): 3/5, Data archival and recipe described, but project code, calibrators, clean settings and scripts missing; custom analysis.
- Rediscovery candidate: no, Project code not printed and several processing details missing, although results are numeric.

## Links

- Method: Hirota et al. 2017 (cite: hirota17) (Ring model fitting of pv diagrams)
- Companion: Pety et al. 2006 (cite: pety06) (Earlier PdBI CO study of HH30)

## Checks

```json
{
 "quotes": 67,
 "quotes_ok": 67,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2013.1.01175.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 80,
  "stated": 48,
  "rate": 0.6
 },
 "evidence_ok": true
}
```
