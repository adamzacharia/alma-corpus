# Accelerating infall and rotational spin-up in the hot molecular core G31.41+0.31

`2018A&A...615A.141B` | Astronomy and Astrophysics 2018 | first author: Beltrán, M. T. | arXiv: 1803.05300 | DOI: 10.1051/0004-6361/201832811

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: Is the compact, unfragmented appearance of the hot molecular core G31.41+0.31 real, and what do its rotation and infall kinematics reveal about its collapse?  
  > "In particular, we investigate whether the compact appearance of G31, with no hint of fragmentation despite its large mass, is real." (Introduction)
- Target **G31.41+0.31**: coordinates RA(J2000)=18h47m34.315s, Dec(J2000)=-01d12m45.90s (phase center)  
  > "The phase reference center of the observations is $\alpha$(J2000)=18$^{\rm h}$47$^{\rm m}$34$s$315, $\delta$(J2000)=$-01^\circ$12$'$45$\ensuremath{''}$90." (Observations); "located at a kinematic distance of 7.9 kpc (Churchwell et al. (cite: churchwell90))" (Introduction); z/distance 7.9 kpc  
  > "The phase reference center of the observations is $\alpha$(J2000)=18$^{\rm h}$47$^{\rm m}$34$s$315, $\delta$(J2000)=$-01^\circ$12$'$45$\ensuremath{''}$90." (Observations); "located at a kinematic distance of 7.9 kpc (Churchwell et al. (cite: churchwell90))" (Introduction); distance from kinematic distance, Churchwell et al. 1990  
  > "The phase reference center of the observations is $\alpha$(J2000)=18$^{\rm h}$47$^{\rm m}$34$s$315, $\delta$(J2000)=$-01^\circ$12$'$45$\ensuremath{''}$90." (Observations); "located at a kinematic distance of 7.9 kpc (Churchwell et al. (cite: churchwell90))" (Introduction)

## Data provenance

- ALMA projects: 2013.1.00489.S
- bands: Band 6 (1.4 mm)  
  > "The observations were performed in Band 6 with the array in an extended configuration." (Observations)
- frequencies and spectral setup: 13 spectral windows covering SiO (5-4), CH3CN (12-11), CH3(13)CN (12-11), CH3CN v8=1, 13CH3CN (13-12)  
  > "The digital correlator was configured in thirteen spectral windows (SPW)" (Observations)
- continuum bandwidth: 1875 MHz window centered at 218 GHz used for continuum  
  > "The total bandwidth of the spectral window used to estimate the continuum is 1875 MHz" (Observations)
- arrays: _not stated_
- configurations: extended configuration  
  > "with the array in an extended configuration" (Observations)
- baselines: _not stated_
- angular resolution: ~0.22" (~1700 au); continuum beam 0.25"x0.19"  
  > "The resulting synthesized CLEANed beam of the maps is $0.25\ensuremath{''}\times0.19\ensuremath{''}$ for the continuum" (Observations)
- max recoverable scale: _not stated_
- sensitivity: continuum rms 1.5 mJy/beam; line rms ~1.3 mJy/beam (2.7 km/s), ~1.6 (0.66 km/s), ~2.1 (0.33 km/s)  
  > "The rms noise of the maps is 1.5 mJy beam$^{-1}$ for the continuum" (Observations)
- time on source: _not stated_
- observing dates: July and September 2015, Cycle 2  
  > "carried out with ALMA in Cycle 2 in July and September 2015" (Observations)
- pi or archival as stated: PI R. Cesaroni; data previously presented by Cesaroni et al. 2017  
  > "we analyze in more detail the ALMA observations of G31 previously presented by Cesaroni et al. ((cite: cesa17))" (Introduction)
- Line: CH3CN 12-11 (ground and v8=1) (not stated)
- Line: 13CH3CN 13-12 (not stated)
- Line: SiO 5-4 (not stated)
- Line: CH3OCHO ~40 unblended transitions, v=0 and vt=1 (not stated)
- Line: H2CO 3_0,3-2_0,2; 3_2,2-2_2,1; 3_2,1-2_2,0 (not stated)
- External data: Dust absorption coefficient kappa_nu=0.008 cm2/g at 217 GHz (gas-to-dust 100)  
  > "$k_\nu$=0.008 cm$^{2}$ g$^{-1}$ (Ossenkopf & Henning (cite: ossenkopf94) and a gas-to-dust mass ratio of 100)" (Analysis) [from Ossenkopf & Henning (cite: ossenkopf94)]
- External data: 12C/13C = 47 at galactocentric distance 4.5 kpc  
  > "the relative abundance of \[$^{12}$C/$^{13}$C\] at the galactocentric distance of 4.5 kpc of G31 would be 47" (Discussion) [from Milam et al. (cite: milam05)]
- External data: CH3OCHO desorption temperature ~70 K  
  > "estimated that CH$_3$OCHO desorbs at a temperature of about 70 K" (Analysis) [from Burke et al. (cite: burke15)]
- External data: A_vib = 1.6e-2 s^-1 for CH3CN  
  > "$A_{\rm vib}$$= 1.6\times10^{-2}$ s$^{-1}$ of Koivusaari et al." (Discussion) [from Koivusaari et al. (cite: koivusaari92)]

## Processing

### Calibration

- pipeline or manual: Calibrated with CASA; details deferred to Cesaroni et al. 2017  
  > "The data were calibrated and imaged using the CASA[^2] software package" (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CLEAN; 13 data cubes  
  > "A total of 13 individual data cubes were created using the CLEAN task" (Observations)
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0.5  
  > "the ROBUST parameter of Briggs ((cite: briggs95)) set equal to 0.5" (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: STATCONT on the 218 GHz window; details in Cesaroni et al. 2017  
  > "The continuum was determined from the broadest spectral window, centered at 218 GHz, using the STATCONT[^4] algorithm" (Observations)
- line free channels: STATCONT continuum channels: 144 (280 MHz) at line-poor to 10 (17 MHz) at line-rich positions  
  > "ranges from 144, which corresponds to a bandwidth of 280 MHz, at line-poor positions, to 10, which corresponds to a bandwidth of 17 MHz" (Observations)
- primary beam correction: Peak intensity and flux density corrected for primary beam response  
  > "Peak intensity and integrated flux density corrected for primary beam response." (Table 1)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.25"x0.19" continuum; 0.25"x0.19" to 0.27"x0.20" lines  
  > "ranges from $0.25\ensuremath{''}\times0.19\ensuremath{''}$ to $0.27\ensuremath{''}\times0.20\ensuremath{''}$ for the lines analyzed in this work" (Observations)
- final rms: 1.5 mJy/beam continuum  
  > "The rms noise of the maps is 1.5 mJy beam$^{-1}$ for the continuum" (Observations)

### Inherited from earlier work

- Detailed observation information and continuum subtraction  
  > "We refer to Cesaroni et al. ((cite: cesa17)) for detailed information on the observations, and, in particular, on the continuum subtraction." (Observations) [from Cesaroni et al. (cite: cesa17)]
- Mass equations for power-law density and temperature  
  > "Following Eqs. (1) and (2) of Beltrán et al. ((cite: beltran02))" (Analysis) [from Beltrán et al. (cite: beltran02)]
- Infall rate estimation method  
  > "Following Beltrán et al. ((cite: beltran06)), we estimated the infall rate inside a solid angle $\Omega$" (Discussion) [from Beltrán et al. (cite: beltran06)]
- Outflow parameter calculation  
  > "Following Cesaroni et al. ((cite: cesa11)), we estimated the outflow parameters from the SiO and CH$_3$CN $v_8=1$ lines" (Discussion) [from Cesaroni et al. (cite: cesa11)]

### Not stated but needed to reproduce (our reading)

- Line-free channel selection and STATCONT settings in detail
- Cell size, image size, masks, clean threshold, deconvolver
- Fixed line widths and source sizes used in each MADCUBA annulus fit
- Isotopic ratios used in XCLASS fits and initial guesses
- Rest frequencies and spectroscopy database used
- Flux calibrator and calibration uncertainty (in Cesaroni et al. 2017)
- Selection of which CH3OCHO lines were fitted
- Outflow velocity intervals and integration details beyond table footnotes

## Analysis recipe

1. **Image cubes and continuum**: CLEAN with Briggs robust 0.5 in CASA; continuum from broadest SPW with STATCONT; further analysis in GILDAS  
  > "Further imaging and analysis were done with the GILDAS[^3] software package." (Observations)
   - software: CASA, GILDAS, STATCONT
   - parameter: robust = 0.5  
  > "the ROBUST parameter of Briggs ((cite: briggs95)) set equal to 0.5" (Observations)
   - fitting: _not stated_
   - validation: High continuum rms attributed to dynamic range, not STATCONT  
  > "the high rms noise of such map is due to dynamic range problems and not to the STATCONT method used to subtract the continuum" (Observations)
2. **Measure continuum core properties**: Core position, flux, FWHM from 50% contour area; deconvolved assuming Gaussians; elliptical Gaussian fit  
  > "Deconvolved diameter, calculated assuming that the cores are symmetric Gaussians" (Table 1)
   - assumption: Distance 7.9 kpc  
  > "The distance to G31 is assumed to be 7.9 kpc." (Table 1)
   - fitting: _not stated_
   - validation: _not stated_
3. **LTE fits of CH3OCHO in annuli for T and N profiles**: Mean spectra over concentric annuli of beam width up to 1.54"; fit CH3OCHO v=0 and vt=1 with MADCUBA; power-law fits to profiles; N_H2 from dust continuum  
  > "we have computed mean spectra over circular concentric annuli of width equal to that of the synthesized beam ($\sim$$0.22\ensuremath{''}$), up to a maximum radius of $1.54\ensuremath{''}$" (Analysis)
   - software: MADCUBA, XCLASS
   - parameter: line width and source size fixed (source larger than beam); dust continuum temperature = azimuthally averaged brightness temperature  
  > "The fitting strategy we adopted in MADCUBA was to fix the line width to a value that provides a good visual fit, and the source size, that we assumed to be larger than the beam size." (Analysis)
   - assumption: Spherical symmetry; LTE; dust temperature = CH3OCHO Tex for N_H2  
  > "we have assumed spherical symmetry for the G31 core, consistent with its roundish appearance" (Analysis)
   - fitting: Least-squares linear fits in log-log; innermost ring N fixed to 2e18 cm-2 by linear extrapolation  
  > "we fixed the column density to $2\times10^{18}$ cm$^{-2}$, the value obtained from linear extrapolation of the column densities at the two adjacent inner rings" (Analysis)
   - validation: Compared T profile with models; checked abundance drop against desorption temperature  
  > "which is much lower than the excitation temperatures estimated in the outer rings of G31 ($>110$ K)" (Analysis)
4. **Estimate core mass**: Optically thin Rayleigh-Jeans dust emission with power-law density and temperature (Beltrán et al. 2002)  
  > "assuming that the dust emission is optically thin and in the Rayleigh-Jeans regime" (Analysis)
   - parameter: r_c=8500 au, q=0.77, T_c=146 K, nu=217 GHz, S_nu=3.10 Jy, n=2  
  > "we adopted $q$=0.77 and $T_c$=146 K (see Eq. \[[\[tex\]](#tex)\]), $\nu$=217 GHz" (Analysis)
   - assumption: kappa=0.008 cm2/g, gas-to-dust 100, n=2 intermediate between 2.2 and 1.5  
  > "Therefore, we assumed an intermediate value of $n=2$." (Analysis)
   - fitting: _not stated_
   - validation: Mass taken as lower limit if dust is optically thick  
  > "the value derived has to be taken as a lower limit in case this condition is not satisfied" (Analysis)
5. **Rotation kinematics from moment maps and PV plots**: Moment maps and PV cuts along PA=68 deg for transitions with different Eup; PV ratio of v8=1 to 13CH3CN K=2  
  > "position-velocity (PV) plots along PA = 68$^\circ$ for the same transitions as in Fig. [4]" (Discussion)
   - software: GILDAS
   - fitting: _not stated_
   - validation: Compared with Girart et al. 2009 PV plots  
  > "in agreement with our findings" (Discussion)
6. **Outflow parameters and test of outflow vs rotation**: SiO and CH3CN v8=1 outflow mass, momentum, energy following Cesaroni et al. 2011  
  > "we assumed a range of temperatures of 20–50 K for SiO and 100–250 K for vibrationally excited CH$_3$CN" (Discussion)
   - parameter: abundances CH3CN 1e-8; SiO 1e-8 to 1e-7; t_dyn ~6e3 yr  
  > "$t_{\rm dyn}\simeq6\times10^3$ yr" (Discussion)
   - fitting: _not stated_
   - validation: Compared with CO and CH3(13)CN values from Cesaroni et al. 2011  
  > "The outflow parameters estimated from SiO for a gas temperature of 50 K are similar to those calculated by Cesaroni et al. ((cite: cesa11))" (Discussion)
7. **Infall velocity vs energy and infall rate**: Velocity of lowest-intensity channel of absorption at continuum peak relative to V_LSR 96.5 km/s; infall rate following Beltrán et al. 2006  
  > "corresponds to that of the spectral channel with the lowest intensity at that position" (Table 3)
   - parameter: radius 1.54", infall velocity 5.1 km/s  
  > "of 5.1 km s$^{-1}$" (Discussion)
   - fitting: _not stated_
   - validation: _not stated_
8. **Model absorption and emission at the core center**: XCLASS fit with background continuum layer, emission layer and foreground absorption layer to CH3CN, 13CH3CN, CH3CN v8=1 on non-continuum-subtracted data  
  > "we modeled the spectrum at the central pixel with three different components" (Discussion)
   - software: XCLASS
   - parameter: background T_B=132 K; line width and velocity offset fixed; source fills beam  
  > "the temperature of the continuum background layer was assumed to be constant and equal to the brightness temperature $T_{\rm B}=132$ K" (Discussion)
   - assumption: LTE; extended foreground filling beam  
  > "We assumed that the foreground or absorption component is extended and that it fills the beam" (Discussion)
   - fitting: _not stated_
   - validation: Same fit for ring at 1.32" (background 1.8 K) to check 12C/13C  
  > "we fitted both the CH$_3$CN and $^{13}$CH$_3$CN emission in a ring located at a distance of $1.32\ensuremath{''}$ from the center of the core" (Discussion)

## Software

- **CASA** : calibration and imaging  
  > "The data were calibrated and imaged using the CASA[^2] software package" (Observations)
- **GILDAS** : further imaging and analysis  
  > "Further imaging and analysis were done with the GILDAS[^3] software package." (Observations)
- **STATCONT** : continuum determination  
  > "using the STATCONT[^4] algorithm" (Observations)
- **MADCUBA** : LTE fits of CH3OCHO in annuli  
  > "we have used MADCUBA because the fitting algorithm converges faster than XCLASS" (Analysis)
- **XCLASS** : LTE fits with absorption at the core center  
  > "to fit the spectra at the core center, where both emission and absorption components are detected, XCLASS is preferred to MADCUBA" (Analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| G31-Main integrated flux density at 1.4 mm | 3.10 | 0.05 | Jy | 2 | 3.10$\pm$0.05 |
| G31-Main deconvolved diameter | 5300 | 300 | au | 2 | 5300$\pm$300 |
| G31-Main peak brightness temperature | 132 | 1 | K | 2 | 132$\pm$1 |
| Tex power-law exponent (Tex ∝ R^-q) | 0.77 | 0.07 | dimensionless | 3 | (2.19\pm0.02) - (0.77\pm0.07)\,\log (R/{\rm arcsec}) |
| H2 column density power-law slope | -1.15 | 0.08 | dimensionless | 3 | (24.01\pm0.02) - (1.15\pm0.08)\,\log (R/{\rm arcsec}) |
| Core mass | ~120 | not stated | Msun | 4 | $M_c$$\simeq120\,M_\odot$ |
| Volume density at core radius | 5.4e6 | not stated | cm-3 | 4 | corresponding to a volume density of $\sim$$5.4\times10^6$ cm$^{-3}$ |
| Velocity gradient CH3CN K=2 | ~50 | not stated | km/s/pc | 5 | The velocity gradient is $\sim$50 km s$^{-1}$ pc$^{-1}$ for CH$_3$CN and CH${_3}^{13}$CN $K$=2 |
| Velocity gradient v8=1 K,l=(6,1) | ~107 | not stated | km/s/pc | 5 | $\sim$107 km s$^{-1}$ pc$^{-1}$ for $K, l=(6, 1)$ $v_8=1$ |
| Infall velocity CH3CN K=2 | 5.1 | 0.2 | km/s | 7 | CH$_3$CN $K$=2 (12–11) / 97 / 5.1$\pm$0.2 |
| Infall accretion rate | Omega/(4pi) x 3e-2 | not stated | Msun/yr | 7 | $\dot M_{\rm inf}=\Omega/(4\,\pi)\,3\times10^{-2}$ $M_\odot\,$yr$^{-1}$ |
| CH3CN emission-layer excitation temperature at center | 151 | -8/+83 | K | 8 | $T_e$ = $151^{-8}_{+83}$ K |
| 12C/13C in the ring away from center and in CH3OCHO | ~10 | not stated | dimensionless | 8 | we estimated the column densities of CH$_3$OCHO and CH$_3$O$^{13}$CHO in the rings not affected by absorption and obtained \[$^{12}$C/$^{13}$C\] $\simeq$10 |

## Qualitative findings

- Main core continuum shows no fragmentation; two free-free sources lie at the center  
  > "this core appears quite round, uniform, and compact, with no hint of fragmentation" (Results)
- Three SiO outflows are found; the CH3CN velocity gradient is attributed to rotation, not outflow  
  > "We conclude that this velocity gradient is produced by rotation of the core." (Discussion)

## Claim tuples

- H: Does the rotation speed up towards the center? | E: Compared PV plots and gradients of lines with different Eup | R: Gradient rises from ~50 to ~107 km/s/pc with energy; slopes ~160 vs ~300 km/s/pc | F: Rotation spins up towards the center | **supported**
- H: Is there accelerating infall? | E: Measured red-shifted absorption velocity vs Eup | R: Absorption velocity increases with energy for CH3CN lines | F: Infall accelerates toward the center, consistent with free-fall collapse | **supported**
- H: Is CH3OCHO abundance drop real? | E: Compared N_CH3OCHO and N_H2 profiles | R: Abundance constant ~4e-7 for R<5000 au, falls as R^-3.2 outside | F: CH3OCHO is concentrated in the inner regions | **supported**
- H: Is the monolithic appearance real? | E: Compared Jeans length with free-free source separation and considered continuum opacity | R: Jeans length 1300-2000 au comparable to 1600 au separation; dust optically thick | F: Likely an unstable fragmenting core hidden by high opacity and limited resolution | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: XCLASS used for center because it treats the core as a background continuum with radiative interaction; MADCUBA used for emission-only fits because it converges faster  
  > "This approach resembles our scenario where all the components along the line of sight interact radiatively." (Analysis)
- Alternative: Single wide-angle NE-SW SiO outflow rejected since it should be seen in single-dish maps  
  > "However, we tend to exclude this possibility, because such a prominent outflow should be clearly seen in single-dish maps of the region" (Results)
- How they decided it was enough: _not stated_
- Limitation (authors): Dust optically thick so N_H2 and mass are lower limits  
  > "Therefore, the H$_2$ column density values should be taken as lower limits." (Analysis)
- Limitation (authors): Interferometer filters out extended emission  
  > "our ALMA observations can miss extended emission" (Discussion)
- Caveat (inferred, ours): Distance of 7.9 kpc is uncertain (maybe ~5 kpc), scaling mass and luminosity
- Caveat (inferred, ours): Annulus-averaged spherical assumption and manual fits with many fixed parameters limit reproducibility
- Caveat (inferred, ours): Infall velocity from the single lowest channel is coarse and affected by blending
- Caveat (inferred, ours): Low 12C/13C partly from saturation and optical depth effects
- Caveat (inferred, ours): Spin-up inferred from different lines possibly tracing different annuli

## Reproducibility

- Data public (paper): ALMA project data cited with ADS/JAO.ALMA#2013.1.00489.S  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00489.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Cell/image size, clean parameters and masks
- Missing: Fixed parameters of each LTE fit
- Missing: Flux calibration and continuum-subtraction details (deferred to Cesaroni et al. 2017)
- Data volume (inferred): ~50-200 GB raw for the Band 6 extended-configuration project
- Score (inferred): 3/5, Public data and main numbers given, but imaging and manual fit details are deferred or unstated.
- Rediscovery candidate: no, Manual LTE fits with many unstated fixed parameters and deferred calibration details make an exact redo hard.

## Links

- Method: Sánchez-Monge et al. 2018 (cite: sanchez-monge18) (STATCONT continuum determination)
- Method: Möller et al. 2017 (cite: moller17) (XCLASS)
- Companion: Cesaroni et al. 2017 (cite: cesa17) (First analysis of the same ALMA survey of six O-type regions)
- Related: ALMA survey of six O-type star-forming regions with hot molecular cores (Cesaroni et al. 2017)

## Checks

```json
{
 "quotes": 92,
 "quotes_ok": 92,
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
  "facts": 95,
  "stated": 65,
  "rate": 0.684
 },
 "evidence_ok": true
}
```
