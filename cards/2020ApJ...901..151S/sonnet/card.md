# Molecular Gas Outflow in the Starburst Galaxy NGC 1482

`2020ApJ...901..151S` | The Astrophysical Journal 2020 | first author: Salak, Dragan | arXiv: 2008.08723 | DOI: 10.3847/1538-4357/abb134

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies
- Question: What are the distribution, dynamics and energetics of molecular gas in the starburst-driven superwind of NGC 1482, and is the wind starburst driven?  
  > "To study the distribution and dynamics of molecular gas in a wind, we imaged the nearby starburst galaxy NGC 1482 in CO ($J=1\rightarrow0$)" (abstract)
- Target **NGC 1482**: coordinates CO peak 3h54m38.917s, -20d30m07.67s (ICRS)  
  > "| Distance | 19.6 Mpc ($1\ensuremath{''}=95$ pc) | \(3\) |" (Table 1); "| $(\alpha,\delta)_\mathrm{ICRS}^\mathrm{CO}$ | $\mathrm{3^h54^m38.917s},-20\ensuremath{^\circ}30\ensuremath{'}07.67\ensuremath{''}$ | \(4\) |" (Table 1); z/distance 19.6 Mpc  
  > "| Distance | 19.6 Mpc ($1\ensuremath{''}=95$ pc) | \(3\) |" (Table 1); "| $(\alpha,\delta)_\mathrm{ICRS}^\mathrm{CO}$ | $\mathrm{3^h54^m38.917s},-20\ensuremath{^\circ}30\ensuremath{'}07.67\ensuremath{''}$ | \(4\) |" (Table 1); distance from Tully 1988 (Tul88)  
  > "| Distance | 19.6 Mpc ($1\ensuremath{''}=95$ pc) | \(3\) |" (Table 1); "| $(\alpha,\delta)_\mathrm{ICRS}^\mathrm{CO}$ | $\mathrm{3^h54^m38.917s},-20\ensuremath{^\circ}30\ensuremath{'}07.67\ensuremath{''}$ | \(4\) |" (Table 1)

## Data provenance

- ALMA projects: 2019.1.01132.S
- bands: Band 3  
  > "Four spectral windows were tuned in band 3 to include the CO (1–0) line at the rest frequency of $\nu_\mathrm{rest}=115.2712018$ GHz and the 100 GHz continuum." (2 Observations)
- frequencies and spectral setup: Four spws with central frequencies 100.6, 102.6, 112.7, 114.6 GHz; 80x60 arcsec mosaic at PA -77 deg  
  > "The 100 GHz continuum visibilities were acquired from TM and ACA over four spectral windows with central sky frequencies of 100.6, 102.6, 112.7, and 114.6 GHz." (2 Observations)
- continuum bandwidth: 6.7 GHz after flagging  
  > "the total synthesized bandwidth after flagging was 6.7 GHz." (2 Observations)
- arrays: 12-m array (TM, 43 antennas) and 7-m ACA (10 antennas), Cycle 7  
  > "The observations were carried out by ALMA in cycle 7 using 43 antennas of the 12-m array (TM) and 10 antennas of the 7-m Atacama Compact Array (ACA)." (2 Observations)
- configurations: _not stated_
- baselines: TM 15-783 m; ACA 9-45 m  
  > "| Baselines (m)             |    15-783     |        9-45        |" (Table 2)
- angular resolution: 1.559" x 1.083" (CO cube); 1.379" x 0.949" (continuum)  
  > "| FWHM $b_\mathrm{maj}$ (arcsec)    |   1.379   |     1.559     |" (Table 3)
- max recoverable scale: 58 arcsec (~5.5 kpc) with ACA  
  > "it was essential to recover large-scale emission using ACA with its short baselines that achieved a maximum recoverable scale of 58$''$ ($\approx5.5$ kpc)." (2 Observations)
- sensitivity: CO 2.1 mJy/beam per 10.16 km/s; continuum 31 uJy/beam  
  > "| Sensitivity rms (mJy beam$^{-1}$) |   0.031   |      2.1      |" (Table 3)
- time on source: TM 27.7 min; ACA 63.5 min  
  > "| On source time (minutes)  |     27.7      |        63.5        |" (Table 2)
- observing dates: TM 2020 Mar 3, 4; ACA 2019 Nov 23, Dec 2  
  > "| Observation date          | 2020 Mar 3, 4 | 2019 Nov 23, Dec 2 |" (Table 2)
- pi or archival as stated: _not stated_
- Line: 12CO J=1-0 (115.2712018 GHz)
- Other facility **Nobeyama 45-m (COMING)**: CO(1-0) total flux for comparison; position angle and stellar extent  
  > "the total flux of the ALMA map is consistent with that obtained by the Nobeyama 45-m telescope" (2 Observations)
- Other facility **2MASS**: K_S image for PA and center  
  > "The position angle of the inner region of the galaxy was estimated from a Two Micron All Sky Survey (2MASS) $K_S$-band" (4.1.1 Position Angle)
- Other facility **Chandra**: Soft X-ray image  
  > "Figure [12](#fig:cohx) (right panel) shows a soft X-ray image, acquired by the *Chandra* telescope" (6.3.2 Hot Ionized Gas)
- Other facility **CTIO 1.5 m**: Halpha and B-band images  
  > "acquired by the Cerro Tololo Inter-American Observatory (CTIO) 1.5 m telescope, that traces warm ($T\sim10^4$ K) ionized gas" (6.3.1 Warm Ionized Gas)
- Other facility **Herschel PACS**: 70 and 100 um dust continuum  
  > "imaged by the PACS instrument on *Herschel* (cite: Ken11)" (6.3.3 Dust)
- External data: Disk position angle -77 deg for mosaic setup  
  > "at a position angle of $-77\ensuremath{^\circ}$ adopted from (cite: Sor19)" (2 Observations) [from (cite: Sor19)]
- External data: Outflow velocity of Halpha gas, mass and energy of ionized outflow  
  > "are $M_\mathrm{w,H\alpha}\gtrsim3.6\times10^5~n^{-1}_\mathrm{e,2}~M_\ensuremath{\odot}$" (5.3 Dynamics) [from (cite: VR02)]
- External data: Supernova rates 0.10, 0.14, 0.03 per yr  
  > "(cite: Kew00) derived a lower value of 0.03 yr$^{-1}$." (6.1 Starburst-Driven Outflow) [from (cite: Str04b), (cite: HS05), (cite: Kew00)]

## Processing

### Calibration

- pipeline or manual: TM and ACA separately calibrated with CASA pipeline  
  > "The TM and ACA data were separately calibrated using the CASA (version 5.6.1-8) pipeline" (2 Observations)
- casa version: CASA 5.6.1-8  
  > "The TM and ACA data were separately calibrated using the CASA (version 5.6.1-8) pipeline" (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: better than 5%  
  > "The accuracy of flux calibration in ALMA band 3 is better than 5%." (2 Observations)
- self calibration: _not stated_

### Imaging

- task: tclean, mosaic mode, TM+ACA combined  
  > "The combined TM and ACA visibilities were then deconvolved together using the task *tclean*." (2 Observations)
- deconvolver: _not stated_
- weighting robust: CO: natural; continuum: Briggs robust 0.5  
  > "with Briggs weighting (robust parameter 0.5)" (2 Observations)
- uv taper: Gaussian FWHM 4" for tapered cube (beam 4.902x4.219", rms 4.1 mJy/beam)  
  > "we created a CO (1–0) data cube by applying a taper (Gaussian of FWHM $4\ensuremath{''}$) on visibilities in the *uv* plane in combination with natural weighting." (6.3 Multiphase Outflow)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub on CO visibilities  
  > "The calibrated CO visibilities were first continuum-subtracted using the CASA task *uvcontsub*." (2 Observations)
- line free channels: _not stated_
- primary beam correction: applied to all data  
  > "Primary beam correction was applied to all ALMA data presented in this paper." (2 Observations)
- array combination: TM and ACA jointly deconvolved; no total power  
  > "Single-dish total power observations were not conducted" (2 Observations)
- smoothing: _not stated_
- final beam: 1.559" x 1.083", PA -61.5 deg (CO)  
  > "$b_\mathrm{maj}=1.559\ensuremath{''}$ (major axis) and $b_\mathrm{min}=1.083\ensuremath{''}$ (minor axis) at a position angle of $-61.5\ensuremath{^\circ}$" (2 Observations)
- final rms: 2.1 mJy/beam at 10.16 km/s via imstat over emission-free channels  
  > "The rms sensitivity at a spectral resolution of 10.16 km s$^{-1}$ is 2.1 mJy beam$^{-1}$" (2 Observations)

### Inherited from earlier work

- SFR from free-free continuum using equations of these works  
  > "Using the equations in these works, assuming an electron temperature of $T_\mathrm{e}=5000~\mathrm{K}$" (3.3 Continuum Emission and Star Formation Rate) [from (cite: Ben15; Mic20)]
- Standard X_CO and low X_CO recommendations  
  > "normalized relative to the standard value of $X_\mathrm{MW}=2.0\times10^{20}~\mathrm{cm^{-2}(K~km~s^{-1})^{-1}}$ for the Galactic disk (cite: BWL13)" (3.1 Molecular Gas Distribution) [from (cite: BWL13)]
- Outflow model modified from CO outflow in M82  
  > "This is a modified version of the model first proposed by (cite: Nak87) to describe the CO outflow in M82" (5.1 Morphology) [from (cite: Nak87)]

### Not stated but needed to reproduce (our reading)

- CO and continuum image sizes and cell sizes
- Deconvolution thresholds, masks and clean parameters
- Line-free channels for uvcontsub and fit order
- Moment-map clipping rms and 3DBarolo input parameters (fit mode, weighting, normalization)
- Exact velocity range and channel setup for cube
- How the outflow CO flux (~70 Jy km/s) was separated from the disk
- Self-calibration status
- Details of K_S image fit region and H-alpha/X-ray image processing

## Analysis recipe

1. **Image CO cube and continuum**: CASA pipeline calibration, uvcontsub, joint TM+ACA tclean mosaic  
  > "The combined TM and ACA visibilities were then deconvolved together using the task *tclean*." (2 Observations)
   - software: CASA
   - parameter: natural weighting, 10.16 km/s channels (CO); Briggs robust 0.5, mfs (continuum)  
  > "The image was then reconstructed using the task *tclean* in mosaic and multi-frequency synthesis modes with Briggs weighting (robust parameter 0.5)." (2 Observations)
   - fitting: _not stated_
   - validation: ALMA total flux consistent with Nobeyama 45-m  
  > "the total flux of the ALMA map is consistent with that obtained by the Nobeyama 45-m telescope" (2 Observations)
2. **Moment maps and molecular gas mass**: Smooth cube to twice beam, clip at 3 sigma as mask, integrate with immoments; mass from CO flux and X_CO  
  > "the data cube was first smoothed to twice the beam size with the CASA task *imsmooth*, and the smoothed cube clipped at $3\sigma$ was applied as a mask to the original cube." (3.1 Molecular Gas Distribution)
   - software: CASA imsmooth, immoments, imfit
   - assumption: X_CO=2.0e20 (standard) or 0.5e20 cm-2 (K km/s)-1; D=19.6 Mpc  
  > "applying the Galactic conversion factor $X_\mathrm{CO}=X_\mathrm{MW}$, the total molecular gas mass in this region is $M_\mathrm{mol}=2.7\times10^9~M_\ensuremath{\odot}$." (3.1 Molecular Gas Distribution)
   - fitting: _not stated_
   - validation: Compared with Sorai et al. 2019 mass, consistent within 15%  
  > "This is consistent within 15% with $2.3\times10^9~M_\ensuremath{\odot}$ in (cite: Sor19)" (3.1 Molecular Gas Distribution)
3. **Continuum sources and star formation rate**: imfit of sources; free-free SFR from 100 GHz flux  
  > "assuming an electron temperature of $T_\mathrm{e}=5000~\mathrm{K}$ and that free-free radiation contributes 80% to the flux at these frequencies" (3.3 Continuum Emission and Star Formation Rate)
   - software: CASA imfit
   - assumption: Te=5000 K; 80% free-free  
  > "assuming an electron temperature of $T_\mathrm{e}=5000~\mathrm{K}$ and that free-free radiation contributes 80% to the flux at these frequencies" (3.3 Continuum Emission and Star Formation Rate)
   - fitting: _not stated_
   - validation: Compared with FIR and Halpha+24um SFRs  
  > "This value is consistent with the SFR derived from far-infrared luminosity, $3.9~M_\ensuremath{\odot}~\mathrm{yr}^{-1}$ in (cite: Kew00)" (3.3 Continuum Emission and Star Formation Rate)
4. **Tilted-ring disk model**: 3DBarolo, 20 rings of 1.56"; PA and center fixed from K_S/CO; phase 1 for i and vsys, phase 2 for vrot and surface brightness  
  > "the computation was conducted in $^\mathrm{3D}$Barolo within 20 elliptical rings of radial width $\Delta R=1.56\ensuremath{''}$ (beam major axis)." (4.2 Two-Phase Computation and Results)
   - software: 3DBarolo, CASA imfit
   - parameter: PA=-74.35 deg from 2MASS K_S imfit  
  > "yielding a position angle of $\mathrm{PA}=-74.35\ensuremath{^\circ}\pm0.43\ensuremath{^\circ}$" (4.1.1 Position Angle)
   - assumption: Coplanar rings with uniform circular motion  
  > "Note that our model is a set of coplanar rings with uniform circular motion in each ring." (4.2 Two-Phase Computation and Results)
   - fitting: 3DBarolo 3D model fit  
  > "The program fits a three-dimensional model to an emission-line data cube." (4.1 Disk Model)
   - validation: pv diagrams of data vs model show no large discrepancies  
  > "We can see that there are no large discrepancies between the data and the model in either direction" (4.2 Two-Phase Computation and Results)
5. **Outflow velocity from residuals and pv diagrams**: Residual velocity = moment 1 minus model; v_w=|dv_p|/(2cos i) from pv cut dC  
  > "derive the deprojected outflow velocity from $v_\mathrm{w}=|\Delta v_\mathrm{p}|/(2\cos{i})$" (5.2 Kinematics)
   - assumption: Outflow perpendicular to disk (theta ~ 0)  
  > "we assume that the outflow observed in panel dC is perpendicular to the galactic disk" (5.2 Kinematics)
   - fitting: _not stated_
   - validation: Consistent with v_z from residuals  
  > "This is consistent with $v_z$, calculated above from the average residual velocity in the streamers" (5.2 Kinematics)
6. **Outflow mass, energy, mass outflow rate**: M_w from outflow CO flux with low X_CO; E=Mv^2/2; Mdot=v M/h_z with h_z=1 kpc  
  > "For $h_z=1$ kpc, the distance that encompasses most of the outflow gas, Equation [\[eq:mor\]](#eq:mor) yields $\dot{M}_\mathrm{w}\sim7~M_\ensuremath{\odot}~\mathrm{yr}^{-1}$." (5.3 Dynamics)
   - assumption: X_CO=0.5e20, alpha_CO=1; cylindrical outflow, constant velocity, uniform density  
  > "Applying a low CO-to-H$_2$ conversion factor of $X_\mathrm{CO}=0.5\times10^{20}\mathrm{cm^{-2}(K~km~s^{-1})^{-1}}$" (5.3 Dynamics)
   - fitting: _not stated_
   - validation: Cylinder geometry gives conservative estimate versus spherical  
  > "we adopt the cylinder geometry that gives a conservative estimate of $\dot{M}_\mathrm{w}$." (5.3 Dynamics)
7. **Energetics, escape velocity and inflow**: Compare E_w with supernova energy (xi~0.1), momentum; singular isothermal sphere escape velocity; inflow rate from halo clouds  
  > "For a timescale of $t_\mathrm{SN}\approx t_\mathrm{w}=1\times10^7~\mathrm{yr}$ and assumed constant $\mathcal{R}_\mathrm{SN}=0.03\mathrm{-}0.14~\mathrm{yr}^{-1}$ and $\xi\sim0.1$" (6.1 Starburst-Driven Outflow)
   - assumption: Singular isothermal sphere truncated at r_max  
  > "we consider a mass distribution described by a singular isothermal sphere" (6.2 Is NGC 1482 Losing Mass?)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.6.1-8: Calibration pipeline, uvcontsub, tclean, imstat, imsmooth, immoments, imfit  
  > "The TM and ACA data were separately calibrated using the CASA (version 5.6.1-8) pipeline" (2 Observations)
- **3DBarolo** : Tilted-ring fit of CO disk  
  > "We derived the basic geometric and kinematic parameters of the molecular gas disk using the code 3D-Based Analysis of Rotating Objects from Line Observations" (4.1 Disk Model)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total CO(1-0) flux | 677 | not stated | Jy km/s | 2 | $\int S_\mathrm{CO}\mathrm{d}v=677~\mathrm{Jy~km~s^{-1}}$ |
| Total molecular gas mass (X_MW) | 2.7e9 | not stated | Msun | 2 | $M_\mathrm{mol}=2.7\times10^9~M_\ensuremath{\odot}$ |
| 100 GHz flux density within r<=10" | 11.3 | not stated | mJy | 3 | $S_\mathrm{100GHz}=11.3~\mathrm{mJy}$ |
| SFR (free-free), central 1 kpc | ~4 | not stated | Msun/yr | 3 | $\mathrm{SFR_{ff}}\approx4~M_\ensuremath{\odot}~\mathrm{yr}^{-1}$ |
| Disk inclination | 76.1 | 2.4 (dispersion) | deg | 4 | the mean value was $i=76.1\ensuremath{^\circ}$ with a dispersion of $\sigma=2.4\ensuremath{^\circ}$ |
| Systemic velocity (LSR) | 1831 | 5 | km/s | 4 | $v_\mathrm{sys}(\mathrm{LSR})=1831\pm5$ km s$^{-1}$ |
| Dynamical mass within 2.9 kpc | 2.21e10 | 0.32e10 | Msun | 4 | $M_\mathrm{dyn}=Rv_\mathrm{rot}^2/G=(2.21\pm0.32)\times10^{10}~M_\ensuremath{\odot}$ |
| Outflow velocity | ~100 | not stated | km/s | 5 | we obtain $v_\mathrm{w}\approx100~\mathrm{km~s^{-1}}$ |
| Outflow CO flux | ~70 | ~30% | Jy km/s | 6 | $\int S_\mathrm{CO}\mathrm{d}v\approx70~\mathrm{Jy~km~s^{-1}}$ with an uncertainty of $\approx30\%$ |
| Outflow mass | ~7e7 | not stated | Msun | 6 | $M_\mathrm{w}\sim7\times10^7~M_\ensuremath{\odot}$ |
| Outflow kinetic energy | ~7e54 | not stated | erg | 6 | $E_\mathrm{w}=M_\mathrm{w}v_\mathrm{w}^2/2\sim7\times10^{54}~\mathrm{erg}$ |
| Mass outflow rate | ~7 | not stated | Msun/yr | 6 | $\dot{M}_\mathrm{w}\sim7~M_\ensuremath{\odot}~\mathrm{yr}^{-1}$ |
| Mass loading factor | ~2 | not stated | dimensionless | 6 | $\dot{M}_\mathrm{w}/\mathrm{SFR}\sim2$ |
| Escape velocity at 2.9 kpc | 250-390 | not stated | km/s | 7 | we get $v_\mathrm{esc}(r)\approx250\mathrm{-}390$ km s$^{-1}$ at $r=30.4\ensuremath{''}$ (2.9 kpc) |
| Molecular mass inflow rate | ~0.2 | not stated | Msun/yr | 7 | the mass inflow rate becomes $\dot{M}_\mathrm{in}\sim0.2~M_\ensuremath{\odot}~\mathrm{yr}^{-1}$ |

## Qualitative findings

- CO outflow forms a cylindrical envelope outside the Halpha and soft X-ray gas, offset by 0.4-1 kpc  
  > "CO gas is distributed approximately as a cylindrically symmetrical envelope surrounding the warm and hot ionized gas traced by H$\alpha$ and soft X-rays." (abstract)

## Claim tuples

- H: Is there a molecular gas outflow in NGC 1482? | E: ALMA+ACA CO(1-0) mosaic, 3DBarolo disk model, residual velocities and pv diagrams | R: Streamers up to 1.5 kpc above disk with blueshifted residuals and v~100 km/s | F: Molecular biconical outflow detected from central 1 kpc | **supported**
- H: Is the wind starburst driven? | E: Compare wind energy and momentum with supernova input | R: E_w ~1% of released energy, Mdot/SFR~2 | F: Starburst feedback can drive the wind | **supported**
- H: Will molecular gas escape? | E: Escape velocity from isothermal sphere vs v_w | R: v_w~100 vs v_esc 250-390 km/s | F: Most molecular gas bound, likely fountain | **supported**

## Reasoning

- Why this data: ACA needed to recover large-scale low-brightness emission of the superwind  
  > "Since superwinds are generally low-brightness, extended structures, it was essential to recover large-scale emission using ACA" (2 Observations)
- Why this method: _not stated_
- Alternative: Halo clouds may be tidal debris from NGC 1481 rather than fountain inflow  
  > "Another possibility is that these halo clouds are tidal debris inflowing from the direction of the nearby galaxy NGC 1481" (5.2 Kinematics)
- How they decided it was enough: _not stated_
- Limitation (authors): Electron density of ionized gas is uncertain, and xi is difficult to estimate  
  > "the value of $\xi$ is generally difficult to estimate" (6.1 Starburst-Driven Outflow)
- Caveat (inferred, ours): Outflow mass depends on a low X_CO, uncertain by factor ~4
- Caveat (inferred, ours): Outflow flux separation and h_z choice are subjective
- Caveat (inferred, ours): Outflow velocity from a single pv cut with assumed theta=0
- Caveat (inferred, ours): Moment-1 residuals mix non-circular motions with vertical flows

## Reproducibility

- Data public (paper): ALMA data acknowledged by project code  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2019.1.01132.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Clean parameters, image/cell sizes
- Missing: 3DBarolo settings
- Missing: Outflow flux extraction regions
- Missing: pv cut definitions
- Data volume (inferred): ~50-100 GB raw (TM+ACA band 3 mosaic)
- Score (inferred): 3/5, Data and main steps stated, but many imaging and modelling parameters and outflow extraction regions unspecified.
- Rediscovery candidate: yes, Public Cycle 7 data, tclean plus 3DBarolo recipe, numeric results (inclination, Mdyn, outflow mass/rate).

## Links

- Method: (cite: DTF15) (3DBarolo)
- Companion: (cite: Sor19) (Nobeyama COMING CO map)
- Companion: (cite: VR02) (Halpha outflow properties)
- Related: COMING

## Checks

```json
{
 "quotes": 89,
 "quotes_ok": 89,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 15,
 "numeric_problems": 0,
 "fill": {
  "facts": 88,
  "stated": 65,
  "rate": 0.739
 },
 "evidence_ok": true
}
```
