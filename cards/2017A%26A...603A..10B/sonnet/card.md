# Fragmentation and disk formation in high-mass star formation: The ALMA view of G351.77-0.54 at 0.06'' resolution

`2017A&A...603A..10B` | Astronomy and Astrophysics 2017 | first author: Beuther, H. | arXiv: 1703.07235 | DOI: 10.1051/0004-6361/201630126

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: How does the high-mass hot core G351.77-0.54 fragment, and what are the kinematics, temperature structure and gravitational stability of its central disk-like structure at 0.06'' resolution?  
  > "We resolve the small-scale structure around the high-mass hot core region G351.77-0.54 to investigate its disk and fragmentation properties." (abstract)
- Target **G351.77-0.54 (IRAS 17233-3606)**: coordinates RA 17:26:42.568, Dec -36:09:17.6 (J2000, phase center)  
  > "The phase center of the observations was R.A. (J2000.0) $17^{\rm{h}}26^{\rm{m}}42.568^{\rm{s}}$ and Dec.  (J2000.0) $-36^{\circ}09'17.6''$." (Observations); "The first estimated luminosity of $\sim 10^5$ L$_{\odot}$ is based on a kinematic distance of 2.2 kpc determined by (cite: norris1993)" (G351.77-0.54 (IRAS 17233-3606):); z/distance 2.2 kpc (alternative 1.0 kpc)  
  > "The phase center of the observations was R.A. (J2000.0) $17^{\rm{h}}26^{\rm{m}}42.568^{\rm{s}}$ and Dec.  (J2000.0) $-36^{\circ}09'17.6''$." (Observations); "The first estimated luminosity of $\sim 10^5$ L$_{\odot}$ is based on a kinematic distance of 2.2 kpc determined by (cite: norris1993)" (G351.77-0.54 (IRAS 17233-3606):); distance from kinematic distance from Norris et al. 1993; 1 kpc from Leurini et al. 2011  
  > "The phase center of the observations was R.A. (J2000.0) $17^{\rm{h}}26^{\rm{m}}42.568^{\rm{s}}$ and Dec.  (J2000.0) $-36^{\circ}09'17.6''$." (Observations); "The first estimated luminosity of $\sim 10^5$ L$_{\odot}$ is based on a kinematic distance of 2.2 kpc determined by (cite: norris1993)" (G351.77-0.54 (IRAS 17233-3606):)

## Data provenance

- ALMA projects: 2013.1.00260.S
- bands: Band 9 (690 GHz)  
  > "observed with ALMA in cycle 2 in the 690 GHz band with 42 antennas in the array" (Observations)
- frequencies and spectral setup: LO 684.405 GHz; four spws of 1.875 GHz, 488 kHz resolution (~0.21 km/s); centers 677.185, 679.479, 691.478, 693.867 GHz  
  > "The receivers were tuned to an LO frequency of 684.405 GHz with four spectral windows distributed evenly in the lower and upper sideband." (Observations); "The central frequencies of the four windows are 677.185, 679.479, 691.478, and 693.867 GHz, respectively" (Observations)
- continuum bandwidth: _not stated_
- arrays: 42 antennas, one execution  
  > "observed with ALMA in cycle 2 in the 690 GHz band with 42 antennas in the array" (Observations)
- configurations: _not stated_
- baselines: 40 m to ~1.6 km  
  > "This results in a baseline length coverage from 40 m up to almost $\sim$1.6 km." (Observations)
- angular resolution: 0.06'' continuum, 0.07'' line  
  > "we achieve spatial resolution elements of $0.06''$ and $0.07''$ for the continuum and line data, respectively" (Observations)
- max recoverable scale: ~2.7''  
  > "allows us to recover spatial scales between approximately $0.06''$ and $2.7''$" (Observations)
- sensitivity: 1 sigma rms 7 mJy/beam continuum; 30 mJy/beam line at 0.5 km/s  
  > "The $1\sigma$ rms of the 438 $\mu$m continuum and spectral line maps at 0.5 km s$^{-1}$ resolution are 7 mJy beam$^{-1}$ and 30 mJy beam$^{-1}$" (Observations)
- time on source: 35 min on target (1 h 40 min execution)  
  > "The total duration of that one execution of one scheduling block was 1 h 40 min with an on-target time of 35 min." (Observations)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CH3CN 37k-36k, k=0-10 (678.659-679.947 GHz)
- Line: CH3(13)CN 37k-36k, k=0-7 (678.980-679.610 GHz)
- Line: CO 6-5 (not stated)
- External data: Large-scale 870 um gas mass of ~664 Msun at 1 kpc, 25 K  
  > "From large-scale 870 $\mu$m continuum emission, (cite: leurini2011b) estimate a gas mass reservoir of $\sim$664 M$_{\odot}$ for a distance of 1 kpc and a temperature of 25 K." (G351.77-0.54 (IRAS 17233-3606):) [from (cite: leurini2011b)]
- External data: Dust opacity kappa_438um = 6.3 cm2/g extrapolated to 1e6 cm-3  
  > "we use a dust opacity $\kappa_{438\mu\rm{m}}=6.3$ cm$^2$ g$^{-1}$, extrapolated for densities of $10^6$ cm$^{-3}$ from (cite: ossenkopf1994)" (3.1) [from (cite: ossenkopf1994)]
- External data: Systemic velocity vlsr = -3.63 km/s  
  > "we use as a reference $v_{\rm{lsr}}$ a value of $-3.63$ km s$^{-1}$ measured for CH$_3$CN$(12_2-11_2)v_8=1$ by (cite: leurini2011)" (G351.77-0.54 (IRAS 17233-3606):) [from (cite: leurini2011)]

## Processing

### Calibration

- pipeline or manual: CASA with ALMA-delivered reduction script  
  > "The calibration was conducted in CASA version 4.3.1 with the ALMA-delivered reduction script." (Observations)
- casa version: CASA 4.3.1  
  > "The calibration was conducted in CASA version 4.3.1 with the ALMA-delivered reduction script." (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Pallas (bandpass J1924-2914; gain J1717-3342)  
  > "Bandpass calibration was conducted with observations of J1924-2914, and the absolute flux was calibrated with observations of Pallas." (Observations)
- flux scale uncertainty: _not stated_
- self calibration: Tested (solint 30 s and shorter), no improvement; not applied  
  > "since that did not improve the data, we used the non-self-calibrated data." (Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: robust = -2 continuum; robust = 0.5 line  
  > "Applying a robust weighting of -2 for the continuum data and a robust weighting of 0.5 to increase the signal-to-noise ratio for the line data" (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: Continuum excludes spw1 and 690.537-690.634, 691.357-691.870, 692.042-692.417 GHz in spw0  
  > "we avoided the strongest line emission features (spw1 for the main CH$_3$CN emission, and the strongest features in spw0 – 690.537 to 690.634 GHz, 691.357 to 691.870 GHz and 692.042 to 692.417 GHz)" (Observations)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.06'' continuum, 0.07'' line  
  > "we achieve spatial resolution elements of $0.06''$ and $0.07''$ for the continuum and line data, respectively" (Observations)
- final rms: 7 mJy/beam continuum; 30 mJy/beam line (0.5 km/s)  
  > "are 7 mJy beam$^{-1}$ and 30 mJy beam$^{-1}$ (corresponding to brightness temperature sensitivities of $\sim$5.1 K and $\sim$16.0 K)" (Observations)

### Inherited from earlier work

- Disk-geometry correction to infall rate (solid angle Omega/4pi)  
  > "we hypothesize a 2D disk-like geometry to refine the infall rate estimate following (cite: beuther2013b)" (3.3.2) [from (cite: beuther2013b)]
- Outflow/disk opening angles of 120 and 60 deg  
  > "Following (cite: kuiper2012; kuiper2015; kuiper2016), an outflow covers approximately an opening angle of $120^{\circ}$ while the disk covers $\sim$60$^{\circ}$" (3.3.2) [from (cite: kuiper2012; kuiper2015; kuiper2016)]
- Optically thin dust mass/column density method  
  > "we can estimate lower limits of the column densities and masses following the outline of (cite: hildebrand1983) or (cite: schuller2009)" (3.1) [from (cite: hildebrand1983; schuller2009)]

### Not stated but needed to reproduce (our reading)

- Channel/line selection and fitting ranges, priors and initial parameters for XCLASS pixel-by-pixel fits
- Image size, cell size, deconvolver, masks and clean threshold
- Self-calibration and flux-scale uncertainty details
- Continuum frequency used for the 438 um image (collapsed channels list)
- How the Toomre Q uncertainties/epicyclic frequency were computed per pixel and inclination
- Exact pv-cut width and position angle

## Analysis recipe

1. **Measure continuum sources**: 438 um continuum image from line-avoided channels; peak positions, fluxes, Planck brightness temperatures; integrated flux within 4 sigma contours  
  > "Table [\[cont_table\]](#cont_table) presents the peak positions, the corresponding peak flux densities and Planck brightness temperatures as well as the total fluxes integrated within the $4\sigma$ contour levels." (3.1)
   - software: CASA
   - fitting: _not stated_
   - validation: Compared with a near line-free sub-band; fluxes agree within 10-20%  
  > "we find that the continuum fluxes largely agree within 10% increasing at most to 20% difference" (Observations)
2. **Derive dust column densities and masses**: Optically thin dust emission following Hildebrand/Schuller  
  > "assuming optically thin emission from thermally emitting dust grains we can estimate lower limits of the column densities and masses" (3.1)
   - parameter: T = 200 K; kappa_438um = 6.3 cm2/g  
  > "a conservative hot core temperature of 200 K is used for all calculations here" (3.1)
   - assumption: gas-to-dust ratio 150; distance 2.2 kpc (1.0 kpc alternative)  
  > "we use a gas-to-dust mass ratio of 150 (cite: draine2011)" (3.1)
   - fitting: _not stated_
   - validation: _not stated_
3. **Outflow and CH3CN kinematics**: CO(6-5) channel maps, red lobe integrated 25-42 km/s; CH3CN first-moment maps and pv cuts perpendicular to outflow, compared with Keplerian curves for 10 (4.5) Msun  
  > "we do clearly identify a red-shifted outflow lobe in the velocity regime from 25 to 42 km s$^{-1}$" (3.2); "the pv-diagram also shows the expected signature for a Keplerian disk around a 10(4.5) M$_{\odot}$ star at 2.2(1) kpc" (3.3.1)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
4. **Infall rate toward source #2**: Spherical Mdot = 4 pi r^2 rho v_in from red-shifted absorption, then scaled by disk solid angle  
  > "we can estimate the mass infall rate with $\dot{M}_{\rm{in}} = 4\pi r^2
\rho v_{\rm{in}}$" (3.3.2)
   - parameter: r ~80 AU, rho ~2.3e9 cm-3, v_in ~7.1 km/s  
  > "The infall velocity can be estimated to $\sim$7.1 km s$^{-1}$" (3.3.2)
   - assumption: spherical symmetry; disk covers ~50% (~2 pi)  
  > "full integration results in approximately 50% or $\sim 2\pi$ being covered by the disk-like structure" (3.3.2)
   - fitting: _not stated_
   - validation: _not stated_
5. **Gas temperature map**: Pixel-by-pixel LTE fit of CH3CN and CH3(13)CN k-ladders, two components, hot component used  
  > "This tool models the data by solving the radiative transfer equation for an isothermal homogeneous object in local thermodynamic equilibrium (LTE) in one dimension" (3.4)
   - software: XCLASS, MAGIX, CASA
   - assumption: LTE, isothermal homogeneous  
  > "isothermal homogeneous object in local thermodynamic equilibrium (LTE) in one dimension" (3.4)
   - fitting: MAGIX optimizer; single vs double component tested  
  > "Temperature results for the central area of interest varied by less than 10% between the single- and double-component fits." (3.4)
   - validation: Temperatures vary <10% between 1- and 2-component fits; residuals attributed to other species  
  > "Temperature results for the central area of interest varied by less than 10% between the single- and double-component fits." (3.4)
6. **Toomre Q map**: Q = c_s kappa/(pi G Sigma) per pixel with Keplerian Omega for 10 Msun, Sigma from the continuum; three temperature prescriptions  
  > "we estimate the Toomre $Q$ parameter for the whole rotating structure around the main source #1 calculating the sound speed $c_s=\sqrt{kT/(2.3m_H)}$" (4.4)
   - parameter: T = T_rot; T = 200 K; T ∝ r^-0.4 with 1400 K at 10 AU  
  > "we use a dust temperature distribution with an approximate dust sublimation temperature of 1400 K at 10 AU" (4.4)
   - assumption: Keplerian rotation around 10 Msun  
  > "using the Keplerian velocity $\Omega$ around a 10 M$_{\odot}$ star" (4.4)
   - fitting: _not stated_
   - validation: Three temperature approaches bracket real Q  
  > "we can consider these Toomre $Q$ maps as the bracketing values for the real physical Toomre $Q$ values in this region." (4.4)

## Software

- **CASA** 4.3.1 (calibration); 4.6 (XCLASS fitting): Calibration, imaging and processing  
  > "Imaging and further data processing was also conducted in CASA." (Observations)
- **XCLASS** 1.2.0: Pixel-by-pixel LTE fitting of CH3CN k-ladders  
  > "To fit our data we used the XCLASS version 1.2.0 with CASA version 4.6." (3.4)
- **MAGIX** : Model optimizer within XCLASS  
  > "It furthermore uses the model optimizer package MAGIX" (3.4)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Peak brightness temperature source #1 | 201 | not stated | K | 1 | / #1 / 17:26:42.534 / -36:09:17.38 / 0.255 / 201 / 2.33 / 6.2 / 0.49 / |
| Mass of source #1 (200 K, 2.2 kpc) | 0.49 | not stated | Msun | 2 | / #1 / 17:26:42.534 / -36:09:17.38 / 0.255 / 201 / 2.33 / 6.2 / 0.49 / |
| Infall rate toward #2 (spherical) | 1.6e-3 | not stated | Msun/yr | 4 | approximate mass infall rates toward submm source #2 of $\dot{M}_{\rm{in}} \sim 1.6\times
10^{-3}$ M$_{\odot}$ yr$^{-1}$ |
| Disk infall rate toward #2 | 0.8e-3 | not stated | Msun/yr | 4 | disk infall rates around $\dot{M}_{\rm{disk,in}}\sim 0.8\times 10^{-3}$  M$_{\odot}$ yr$^{-1}$ at 2.2 kpc distance |
| CH3CN gas temperature | largely ~1000 | not stated | K | 5 | We find very warm gas with temperatures largely around 1000 K with no steep gradient. |
| Toomre Q minimum, T∝r^-0.4 case | >~1.5 | not stated | dimensionless | 6 | even the lowest values in the map derived with the temperature distribution are greater than $\sim$1.5 |
| Source density | 1.8e4 (2.2 kpc) to 2.0e5 (1 kpc) | not stated | pc-3 | 1 | source densities of $\sim 1.8\times
10^4$ pc$^{-3}(2.0\times 10^5$ pc$^{-3}$) at 2.2(1) kpc distance |

## Qualitative findings

- CO(6-5) red-shifted outflow lobe NNW of source #1; CH3CN velocity gradient perpendicular to it  
  > "The kinematic analysis of the CH$_3$CN data identifies a velocity gradient perpendicular to that outflow." (Conclusions)

## Claim tuples

- H: Does the region fragment strongly on small scales? | E: 438 um continuum at 0.06'' | R: Four sources; #1 and #2 within ~500 AU, no further fragmentation of #1 | F: Proto-Trapezium-like system with high source density | **supported**
- H: Is there a rotating disk-like structure? | E: CH3CN moment maps and pv diagrams | R: Velocity gradient with partly Keplerian-like signatures, plus envelope/outflow contributions | F: Rotating disk embedded in infalling envelope, possibly outflow-influenced | **partially**
- H: Do gas and dust temperatures agree? | E: XCLASS CH3CN temperature vs continuum brightness temperature | R: Gas ~1000 K vs dust <=201 K | F: Dust may trace the mid-plane and gas the hotter surface layer | **partially**
- H: Is the central structure gravitationally stable? | E: Pixel-wise Toomre Q | R: Q > ~1.5 everywhere under all three temperature prescriptions | F: Stable against axisymmetric fragmentation on resolved scales | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Steeper temperature profile alpha=0.5 would give Q<1 but is considered unlikely  
  > "we consider such a steep distribution unlikely considering the deeply embedded phase" (4.4)
- How they decided it was enough: _not stated_
- Limitation (authors): Mass estimates are lower limits due to optical depth and >99% flux filtered out  
  > "indicates that more than 99% of the extended flux is filtered out by our extended baseline ALMA data" (3.1)
- Limitation (authors): Central mass cannot be determined from pv diagrams  
  > "Hence, determining the exact mass of the central object unfortunately remains difficult." (4.2)
- Caveat (inferred, ours): Distance uncertain by factor 2.2, affecting all physical quantities
- Caveat (inferred, ours): Single-execution data with very large spatial filtering
- Caveat (inferred, ours): LTE fit quality poor in example; temperature from optically thick/absorbed region
- Caveat (inferred, ours): Toomre analysis depends on assumed Keplerian mass and temperature prescriptions

## Reproducibility

- Data public (paper): ALMA data identified by project code in acknowledgements  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00260.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: XCLASS fit setup
- Missing: Imaging parameters (cell, size, clean settings)
- Missing: pv cut definition
- Data volume (inferred): ~20-50 GB
- Score (inferred): 5/5, Single public dataset and a clear recipe, but imaging and XCLASS fit details are missing.
- Rediscovery candidate: yes, Public data with numeric continuum and infall results; the recipe is reasonably clear.

## Links

- Method: (cite: moeller2015) (XCLASS)
- Method: (cite: moeller2013) (MAGIX optimizer)
- Companion: (cite: leurini2011) (SMA study of the region, outflows, vlsr)

## Checks

```json
{
 "quotes": 72,
 "quotes_ok": 72,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 81,
  "stated": 51,
  "rate": 0.63
 },
 "evidence_ok": true
}
```
