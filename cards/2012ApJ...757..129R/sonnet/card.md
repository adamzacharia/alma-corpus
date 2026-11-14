# Kinematics of the CO Gas in the Inner Regions of the TW Hya Disk

`2012ApJ...757..129R` | The Astrophysical Journal 2012 | first author: Rosenfeld, Katherine A. | arXiv: 1208.1285 | DOI: 10.1088/0004-637X/757/2/129

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks
- Question: What do the spatially and spectrally resolved 12CO J=2-1 and J=3-2 line wings from the TW Hya disk reveal about the temperature and kinematic structure of the inner disk?  
  > "we are not able to reproduce the intensity of these wings and the general spatio-kinematic pattern of the lines with simple models for the disk structure and kinematics." (abstract)
- Target **TW Hya**: coordinates _not stated_; z/distance nearest classical T Tauri star (distance value not stated)  
  > "the nearest (cite: vanleeuwen07) classical T Tauri star, TW Hya" (1 Introduction); distance from van Leeuwen 2007 (cite: vanleeuwen07)  
  > "the nearest (cite: vanleeuwen07) classical T Tauri star, TW Hya" (1 Introduction)

## Data provenance

- ALMA projects: 2011.0.00001.SV
- bands: Band 6 and Band 7  
  > "using receiver bands 6 and 7 on 2011 April 20 and 22, respectively" (2 Data and Calibration)
- frequencies and spectral setup: four 0.5 GHz spectral windows, 122 kHz channels; CO 2-1 at 230.538 GHz and CO 3-2 at 345.796 GHz; 0.16 and 0.11 km/s spacing  
  > "four 0.5 GHz-wide spectral windows (two in each sideband) with a 122 kHz channel spacing in each window" (2 Data and Calibration)
- continuum bandwidth: ~1 GHz per receiver band  
  > "Two other spectral windows were designed to provide $\sim$1 GHz of continuum bandwidth in each receiver band" (2 Data and Calibration)
- arrays: nine 12-m ALMA antennas (commissioning/SV)  
  > "The TW Hya disk was observed with nine 12-m elements of ALMA as part of the commissioning and SV effort during construction." (2 Data and Calibration)
- configurations: _not stated_
- baselines: ~20-100 m  
  > "antenna spacings providing baseline lengths of $\sim$20-100 m" (2 Data and Calibration)
- angular resolution: 2.8"x2.4" (PA 44 deg) for 2-1; 1.7"x1.5" (PA 22 deg) for 3-2  
  > "synthesized beam of dimensions $2.8\ensuremath{''}\times2.4\ensuremath{''}$ (at a P.A. of 44$^\circ$) for $J$=2$-$1" (2 Data and Calibration)
- max recoverable scale: _not stated_
- sensitivity: per-channel rms 0.008-0.009 Jy/beam (2-1), 0.015-0.020 Jy/beam (3-2)  
  > "0.35 | 0.008 | $7.3\pm0.7$" (Table 1)
- time on source: two ~4.5-hour observations  
  > "two (contiguous) $\sim$4.5-hour observations" (2 Data and Calibration)
- observing dates: 2011 April 20 (Band 6) and 22 (Band 7)  
  > "on 2011 April 20 and 22, respectively" (2 Data and Calibration)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (230.538 GHz)
- Line: 12CO J=3-2 (345.796 GHz)
- Other facility **HST/STIS**: scattered-light azimuthal asymmetry (Roberge et al. 2005) compared with warp model  
  > "wideband *Hubble Space Telescope* (*HST*)/STIS coronagraphic images of optical light reflected off the disk surface" (4 Discussion)
- External data: Scattered-light azimuthal modulation of TW Hya (peak near PA 234, trough near 54 deg)  
  > "with a peak near P.A. = 234$^\circ$ and a trough near 54$^\circ$" (4 Discussion) [from Roberge et al. 2005 (cite: roberge05)]
- External data: Stellar mass 0.8 Msun fixed for fiducial model  
  > "The fiducial stellar mass was fixed to $M_{\ast} = 0.8$ M$_{\odot}$ (cite: wichmann98; hughes11)" (3.2 The Failure of Standard Models) [from (cite: wichmann98; hughes11)]
- External data: CO molecular data from LAMBDA database  
  > "the data from the LAMBDA database (cite: scholier05)" (3.1 Modeling Overview) [from (cite: scholier05)]

## Processing

### Calibration

- pipeline or manual: CASA following ALMA SV team scripts  
  > "carefully following the detailed processing scripts kindly provided by the ALMA science verification team" (2 Data and Calibration)
- casa version: CASA v3.3  
  > "These data were calibrated in the `CASA` software package (v3.3)" (2 Data and Calibration)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan (absolute flux); 3C 279 bandpass; J1037-295 gain  
  > "brief observations were made of Titan for absolute flux calibration" (2 Data and Calibration)
- flux scale uncertainty: ~10% systematic  
  > "The quoted errors include a $\sim$10% systematic uncertainty in the absolute flux scale." (Table 1)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: CLEAN  
  > "deconvolved with the `CLEAN` algorithm using a simple polygon mask applied to all channels" (2 Data and Calibration)
- weighting robust: natural weighting  
  > "Fourier inverted (assuming natural weighting) with modest spectral averaging" (2 Data and Calibration)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: simple polygon mask in all channels  
  > "using a simple polygon mask applied to all channels" (2 Data and Calibration)
- multiscale scales: _not stated_
- continuum subtraction: performed on visibilities; various polynomial orders/channel ranges tested  
  > "varying the polynomial order and channel ranges employed to determine the underlying continuum level" (2 Data and Calibration)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 2.8"x2.4" PA 44 (2-1); 1.7"x1.5" PA 22 (3-2)  
  > "$1.7\ensuremath{''}\times1.5\ensuremath{''}$ (P.A. = 22$^\circ$) for $J$=3$-$2" (2 Data and Calibration)
- final rms: 0.008-0.009 Jy/beam (2-1), 0.015-0.020 (3-2) per channel  
  > "0.20 | 0.009 | $7.8\pm0.8$" (Table 1)

### Inherited from earlier work

- Calibration steps and reference datasets from the ALMA SV team  
  > "Since those instructions, along with fully calibrated measurement sets, are publicly available online[^1], we do not repeat the details here." (2 Data and Calibration) [from ALMA science verification team scripts]
- Fiducial model parameterization motivated by previous TW Hya CO analyses  
  > "motivated by the results of our previous analyses of CO emission from the TW Hya disk (cite: qi04; qi06; hughes08; hughes11; andrews12)" (3.2 The Failure of Standard Models) [from (cite: qi04; qi06; hughes08; hughes11; andrews12)]
- Dust grain properties for scattered-light model  
  > "We adopt the relative mass ratio, grain composition, and size distribution used in the disk atmosphere models of (cite: andrews12)." (4 Discussion) [from (cite: andrews12)]

### Not stated but needed to reproduce (our reading)

- CLEAN threshold, polygon mask geometry, cell and image size
- Exact line-free channels and polynomial order for continuum subtraction
- LIME settings (number of grid points, photons) and CO abundance X_co value
- Gas-to-dust ratio and dust properties details for RADMC-3D model
- Exact MPFIT setup, initial values and how manual adjustments were made
- Distance to TW Hya adopted

## Analysis recipe

1. **Calibrate and image CO cubes**: Calibrate SV data in CASA, continuum-subtract, invert with natural weighting, CLEAN with polygon mask; native and binned channels  
  > "We utilized two different channel spacings: (1) “native", meaning 0.20 and 0.12 km s$^{-1}$ for $J$=2$-$1 and $J$=3$-$2" (2 Data and Calibration)
   - software: CASA
   - parameter: systemic LSR velocity +2.87 km/s forced onto a channel center  
  > "we elected to force the reduced spectral datasets to have a channel precisely centered on the known systemic LSR velocity of TW Hya, $+$2.87 km s$^{-1}$." (2 Data and Calibration)
   - fitting: _not stated_
   - validation: Tested atmospheric CO, flat Tsys re-calibration, and continuum subtraction variations; wings persist  
  > "we re-calibrated the data instead with a spectrally flat, band-averaged $T_{\rm sys}$ correction. This had no discernable effect on the results" (2 Data and Calibration)
2. **Fit fiducial model**: Parametric viscous-disk model with LIME non-LTE radiative transfer, imaged through CASA; MPFIT chi2 minimization on visibilities then manual adjustment  
  > "utilized the modified Levenberg-Marquardt minimization algorithm `MPFIT` (cite: markwardt09) to help find parameters that produced a low $\chi^2$ in the spectral visibilities" (3.2 The Failure of Standard Models)
   - software: LIME, MPFIT, CASA
   - parameter: PA fixed 151 deg; M*=0.8 Msun; inclination free; T10,q free per line  
  > "the major axis position angle was set to 151$^\circ$ (east of north)" (3.2 The Failure of Standard Models)
   - assumption: vertically isothermal, mu=2.37, Keplerian, vr=vz=0  
  > "we implicitly assumed that the disk is vertically isothermal (at each radius)" (3.1 Modeling Overview)
   - fitting: MPFIT chi2 on visibilities, then manual tweaks; priors not stated  
  > "the model parameters were slightly adjusted manually to best reproduce the observed channel maps" (3.2 The Failure of Standard Models)
   - validation: Compare model and data channel maps  
  > "The fiducial model is a good match to the ALMA data near the systemic velocity, but notably fails to reproduce the emission line wings" (3.2 The Failure of Standard Models)
3. **Test high-q, high-M*, high-i models**: Uniformly modify q, M*, or i and compare channel maps  
  > "We constructed such a “high-$q$" model with a larger radial temperature gradient ($q = 0.65$)" (3.2 The Failure of Standard Models)
   - software: LIME
   - parameter: q=0.65; M*=1.5 Msun; i=8 deg  
  > "a more inclined viewing geometry ($i = 8\ensuremath{^\circ}$)" (3.2 The Failure of Standard Models)
   - fitting: _not stated_
   - validation: All reproduce wings but fail near systemic velocity  
  > "No reasonable combinations of $q$, $M_{\ast}$, and $i$ can simultaneously reproduce both the CO line wings and the emission morphology near the systemic velocity." (3.2 The Failure of Standard Models)
4. **Alternative models: hot inner disk, non-Keplerian, warp**: Add radius-dependent temperature scaling, velocity scaling f(r), or inclination i(r); warp via quaternion rotation  
  > "The velocity field is tilted using a quaternion transformation, as described in more detail in the Appendix." (3.3.3 A Disk Warp)
   - software: LIME, CASA
   - parameter: dT=3 inside r_hot=4 AU  
  > "scaling factor $\delta T = 3$ inside a radius $r_{\rm hot} = 
4$ AU" (3.3.1 A Hot Inner Disk)
   - parameter: non-Keplerian: r_b≈60 AU, x=0.15  
  > "Adopting $r_b \approx 60$ AU and $x = 0.15$ to describe $f$" (3.3.2 A Non-Keplerian Velocity Field)
   - parameter: warp: i0≈8 deg at r0=5 AU, y=0.15  
  > "with $i_0 \approx 8\ensuremath{^\circ}$ at $r_0 = 5$ AU and a gradient $y = 0.15$" (3.3.3 A Disk Warp)
   - assumption: vertically thin warped disk aligned with major axis  
  > "aligned with the disk major axis (assuming a vertically thin disk; see the Appendix)" (3.3.3 A Disk Warp)
   - fitting: Qualitative, not optimized  
  > "The {$r_b$, $x$} values adopted here are not unique (nor optimized)" (3.3.2 A Non-Keplerian Velocity Field)
   - validation: Compare channel maps and PV diagrams  
  > "as well as in position-velocity diagrams (constructed from a slice along the disk major axis)" (3.3.1 A Hot Inner Disk)
5. **Test warp against scattered light**: RADMC-3D 0.8 micron image of warp model with dust only outside 4 AU, isotropic scattering; azimuthal profile in 20-deg bins at r=70-88 AU  
  > "we calculated a normalized intensity profile in 20$^\circ$ azimuthal bins in an annular ring from $r = 70$-88 AU." (4 Discussion)
   - software: RADMC-3D
   - assumption: dust and gas co-located outside 4 AU; no dust inside  
  > "assuming that the dust and gas are co-located outside a radius of 4 AU" (4 Discussion)
   - fitting: Not a fit  
  > "this scattered light model is *not* a fit to the *HST*/STIS observations" (4 Discussion)
   - validation: Compared to Roberge et al. azimuthal modulation  
  > "demonstrate a striking resemblance to the azimuthal modulation pattern inferred from the *HST*/STIS data" (4 Discussion)

## Software

- **CASA** v3.3: calibration and imaging of data and models  
  > "These data were calibrated in the `CASA` software package (v3.3)" (2 Data and Calibration)
- **LIME** : 3D non-LTE radiative transfer for CO model cubes  
  > "three-dimensional non-local thermodynamic equilibrium (non-LTE) molecular excitation and radiative transfer code `LIME` (cite: brinch10)" (3.1 Modeling Overview)
- **MPFIT** : Levenberg-Marquardt minimization for fiducial model  
  > "modified Levenberg-Marquardt minimization algorithm `MPFIT` (cite: markwardt09)" (3.2 The Failure of Standard Models)
- **RADMC-3D** v0.30: scattered-light image of warp model  
  > "`RADMC-3D`[^4] (v0.30: C. P. Dullemond) was then used to generate a high-resolution synthetic image" (4 Discussion)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Projected line-wing velocity extent | 2.1 | not stated | km/s | 1 | significant ($>$5 $\sigma$) emission in the wings of both CO transitions out to projected velocities at least $\pm$2.1 km s$^{-1}$ |
| CO 2-1 integrated flux (5"x5" box, 0.20 km/s) | 17.5 | 1.8 | Jy km/s | 1 | $7.8\pm0.8$ / $17.5\pm1.8$ |
| CO 3-2 integrated flux (0.12 km/s) | 37.2 | 3.7 | Jy km/s | 1 | $9.7\pm1.0$ / $37.2\pm3.7$ |
| Hot model temperature scaling | 3 inside 4 AU | not stated | dimensionless | 4 | scaling factor $\delta T = 3$ inside a radius $r_{\rm hot} = 
4$ AU |
| Warp inclination gradient y | 0.15 | not stated | dimensionless | 4 | a gradient $y = 0.15$ |
| Fiducial inclination | 5.8 | not stated | deg | 2 | $i_{10}$ / \[$^\circ$\] / 5.8 / 5.8 / 6.0 / 8.0 / 5.8 |

## Qualitative findings

- Models require a substantial molecular gas reservoir inside ~4 AU where dust optical depths are diminished  
  > "the ALMA data clearly require a substantial molecular gas reservoir located inside the region where dust optical depths are known to be substantially diminished" (abstract)

## Claim tuples

- H: Can standard Keplerian disk models explain CO line wings and core morphology? | E: Fiducial, high-q, high-M*, high-i LIME models compared to ALMA channel maps | R: No single uniform model reproduces both wings and core | F: Standard models fail | **supported**
- H: Do radius-dependent modifications reproduce the data? | E: Hot inner disk, non-Keplerian, warp models | R: All three reproduce wings and core qualitatively | F: Three alternatives work; none uniquely favored | **supported**
- H: Does the warp model explain the HST scattered-light azimuthal asymmetry? | E: RADMC-3D at 0.8 micron of warp model | R: Sinusoidal azimuthal modulation resembling observations | F: Qualitative support for a modest warp, though not unique | **partially**

## Reasoning

- Why this data: TW Hya is nearby, gas-rich and nearly face-on; ALMA SV gives much higher sensitivity  
  > "the TW Hya disk coincidentally has the added benefits of a nearly face-on viewing geometry" (1 Introduction)
- Why this method: Qualitative illustration rather than detailed fitting, awaiting better data  
  > "We focus on a qualitative illustration of how the data reveal novel spatio-kinematic information" (3 Analysis)
- Alternative: Radially varying turbulent width tested with sound-speed scaling; little effect on wings  
  > "given the low $\xi$ at large $r$ and modest radial variation of $c_s$, this has little effect on the CO line wings" (3.4 Additional Comments)
- How they decided it was enough: _not stated_
- Limitation (authors): Model parameters are not unique nor optimized; limited resolution  
  > "the warp model parameters we determine or even the formulation we adopt are not unique, nor optimized" (3.3.3 A Disk Warp)
- Caveat (inferred, ours): No quantitative fit or uncertainties on model parameters
- Caveat (inferred, ours): Degeneracy among temperature, velocity and warp models unresolved
- Caveat (inferred, ours): Low angular resolution (~2") limits spatial constraints
- Caveat (inferred, ours): Scattered-light comparison is qualitative and depends on dust assumptions

## Reproducibility

- Data public (paper): SV data and scripts publicly available online  
  > "those instructions, along with fully calibrated measurement sets, are publicly available online[^1]" (2 Data and Calibration)
- Products in archive: _not stated_
- Missing: LIME configuration and CO abundance
- Missing: Mask and CLEAN parameters
- Missing: Manual model tuning details
- Data volume (inferred): ~10-50 GB (SV calibrated measurement sets, two bands)
- Score (inferred): 3/5, Public data and tabulated model parameters, but modeling set-up details and manual tuning are incomplete.
- Rediscovery candidate: no, Results are qualitative model comparisons and key settings are not fully stated.

## Links

- Method: Brinch & Hogerheijde 2010 (cite: brinch10) (LIME radiative transfer code)
- Method: Markwardt 2009 (cite: markwardt09) (MPFIT)
- Companion: Hughes et al. 2011 (cite: hughes11) (previous TW Hya CO analysis)
- Companion: Andrews et al. 2012 (cite: andrews12) (TW Hya disk structure models)
- Related: ALMA Science Verification

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
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 81,
  "stated": 61,
  "rate": 0.753
 },
 "evidence_ok": true
}
```
