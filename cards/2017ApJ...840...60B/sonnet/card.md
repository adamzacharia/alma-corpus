# A Close-up View of the Young Circumbinary Disk HD 142527

`2017ApJ...840...60B` | The Astrophysical Journal 2017 | first author: Boehler, Y. | arXiv: 1704.00787 | DOI: 10.3847/1538-4357/aa696c

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: What are the radial and azimuthal gas and dust distributions in the HD 142527 circumbinary disk, and do they support dust trapping in a gas pressure bump?  
  > "These results strongly support a scenario in which millimeter dust grains are radially and azimuthally trapped toward the center of a gas pressure bump." (abstract)
- Target **HD 142527**: coordinates _not stated_; z/distance 156 pc +/- 7.5 pc  
  > "HD 142527 is a 2-5 Myr binary system (cite: Fuka2006; Laco2016) at a distance of 156 pc $\pm$ 7.5 pc[^1]." (Introduction); "This distance is based on the stellar parallax measured by the Gaia space telescope" (Introduction); distance from Gaia parallax (Gaia Collaboration 2016)  
  > "HD 142527 is a 2-5 Myr binary system (cite: Fuka2006; Laco2016) at a distance of 156 pc $\pm$ 7.5 pc[^1]." (Introduction); "This distance is based on the stellar parallax measured by the Gaia space telescope" (Introduction)

## Data provenance

- ALMA projects: 2012.1.00725.S
- bands: 0.88 mm (~340-344 GHz continuum)  
  > "Our data contain 4 GHz bandwidth in continuum in the frequency range $\sim$ 340-344 GHz with channel width of 15.625 MHz." (Observations and data reduction)
- frequencies and spectral setup: 13CO and C18O J=3-2 in two spectral windows of 234 MHz, channel width 130 kHz after Hanning smoothing (~0.11 km/s)  
  > "in two different spectral windows of 234 MHz bandwidth and channel width of 130 kHz after Hanning smoothing ($\sim$ 0.11 km s$^{-1}$)." (Observations and data reduction)
- continuum bandwidth: 4 GHz  
  > "Our data contain 4 GHz bandwidth in continuum" (Observations and data reduction)
- arrays: _not stated_
- configurations: _not stated_
- baselines: 35-770 m projected, 37 antennas  
  > "using 37 antennas on projected baselines between 35 and 770 meters." (Observations and data reduction)
- angular resolution: continuum 0.21''x0.26''; lines 0.27''x0.31''  
  > "which delivers a beam size of 0.21$''\times$0.26$''$ (PA = -59$^\circ$)" (Observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: continuum rms 115 uJy/beam; 13CO 5.9 and C18O 7.5 mJy/beam per channel  
  > "an rms noise of 5.9 and 7.5 mJy beam$^{-1}$ per channel for $^{13}$CO J=3-2 and C$^{18}$O J=3-2, respectively." (Observations and data reduction)
- time on source: ~1.1 hour on target (~2.9 hours total)  
  > "with a total time of $\sim$ 2.9 hours and $\sim$ 1.1 hour on target" (Observations and data reduction)
- observing dates: 2015 June 13  
  > "The observations were carried on 2015 June 13th in dual polarization" (Observations and data reduction)
- pi or archival as stated: _not stated_
- Line: 13CO J=3-2 (330.58797 GHz)
- Line: C18O J=3-2 (329.33055 GHz)
- Other facility **Gaia**: distance of 156 pc  
  > "given the new distance of 156 pc measured by Gaia" (Disk dynamic)
- External data: M15 model of dust and gas surface density (Muto et al. 2015), rescaled to 156 pc  
  > "we compare our observations with the M15 model, rescaled to the distance of 156 pc" (Comparison with previous models) [from (cite: Muto2015)]
- External data: 34 GHz flux density of 80 uJy/beam at central source  
  > "A flux density of 80 $\mu$Jy beam$^{-1}$ was detected at 34 GHz at the same position by (cite: Casa2015-2)." (Dust emission) [from (cite: Casa2015-2)]
- External data: fractional abundances 6e-5, 9e-7, 1.35e-7 for CO, 13CO, C18O  
  > "assuming fractional abundances of 6$\times 10^{-5}$, 9$\times 10^{-7}$ and 1.35$\times 
10^{-7}$ for CO, $^{13}$CO and C$^{18}$O respectively (cite: Qi2011)" (On the anti-correlation between dust and molecular line emission) [from (cite: Qi2011)]
- External data: primary star mass 2.4 Msun  
  > "The primary star is an Herbig FeIIIe star with a mass of 2.4 $M_\odot$ (cite: Verh2011)" (Introduction) [from (cite: Verh2011)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline  
  > "The data were calibrated using the ALMA pipeline with the version 4.3.1 of CASA." (Observations and data reduction)
- casa version: CASA 4.3.1 (Software section says v4.3.10)  
  > "The data were calibrated using the ALMA pipeline with the version 4.3.1 of CASA." (Observations and data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan (bandpass J1427-4206, phase J1604-4441)  
  > "the flux calibration was obtained by observing Titan" (Observations and data reduction)
- flux scale uncertainty: _not stated_
- self calibration: phase solint 30 s; amplitude solint = scan length (~5 min); peak S/N improved ~4x in continuum  
  > "We self-calibrated the visibilities for the scientific source by using an interval time of 30 seconds for the phases and equal to the lengths of the scan ($\sim$ 5 minutes) for the amplitude." (Observations and data reduction)

### Imaging

- task: _not stated_
- deconvolver: multi-scale clean, scales 0, 6, 18 pixels  
  > "The image deconvolution was performed using multi-scale cleaning with scale factors of 0, 6, 18 times the pixel size (0.04 $''$)." (Observations and data reduction)
- weighting robust: continuum Briggs -2; lines Briggs 0.5  
  > "For the lines, we used a Briggs factor of 0.5" (Observations and data reduction)
- uv taper: _not stated_
- cell size: 0.04''  
  > "scale factors of 0, 6, 18 times the pixel size (0.04 $''$)" (Observations and data reduction)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub after applying continuum gains to lines  
  > "we applied the complex gains derived from the continuum to the emission lines and subtracted the continuum with the task uvcontsub." (Observations and data reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: continuum 0.21''x0.26'' PA -59; lines 0.27''x0.31'' PA -62  
  > "which gives an angular resolution of 0.27$''\times$0.31$''$ (PA = -62$^\circ$)" (Observations and data reduction)
- final rms: 115 uJy/beam continuum  
  > "the rms is 115 $\mu$Jy beam$^{-1}$" (Observations and data reduction)

### Inherited from earlier work

- Dust opacity 2.9 cm2/g and grain composition/size distribution as in M15  
  > "The dust grain properties are chosen to have a dust opacity of 2.9 g cm$^{-2}$ at 0.88 mm, as in M15." (Comparison with previous models) [from (cite: Muto2015)]
- Modeling of radial profiles along north and south azimuths  
  > "A similar procedure was adopted in modeling previous observations at an angular resolution of $\sim$ 0.45$''$ by (cite: Muto2015)." (Derivation of the gas and dust surface density) [from (cite: Muto2015)]

### Not stated but needed to reproduce (our reading)

- Line-free channels used for uvcontsub
- Fit method/optimizer and goodness-of-fit criterion for the radial profile models (apparently by eye)
- Clean threshold and masks
- Flux scale uncertainty
- Exact CASA version (4.3.1 vs 4.3.10)
- Position angle ranges are inconsistent (16-26 deg in text, written as arcsec in table)
- Primary beam correction details
- Inner disk/dust surface-density scaling for the RADMC-3D model

## Analysis recipe

1. **Calibrate and image continuum and CO lines**: Pipeline calibration, self-calibration, multiscale clean, continuum subtraction  
  > "The data were calibrated using the ALMA pipeline with the version 4.3.1 of CASA." (Observations and data reduction)
   - software: CASA
   - parameter: Briggs -2 continuum, 0.5 lines  
  > "The final map of the continuum was generated using a Briggs factor of -2" (Observations and data reduction)
   - fitting: _not stated_
   - validation: no negative components at source c in residual map  
  > "we verified that no negative components at the position of source $c$ exist in the map of the residual obtained at the end of the deconvolution process." (Dust emission)
2. **Measure morphology, moments, brightness temperature and kinematics**: Moment maps, peak brightness temperature via inverse Planck function, PV diagram Keplerian comparison  
  > "For the conversion of Jy beam$^{-1}$ to Kelvin, we used the inverse of the Planck function" (CO peak emission)
   - software: CASA
   - parameter: moment I excludes pixels below 5 sigma  
  > "They were calculated by excluding pixels with emission below 5 $\sigma$ after subtracting the continuum emission." (3.2 Disk dynamic)
   - assumption: distance 156 pc  
  > "assuming a distance of 156 pc for the system" (Observations and data reduction)
   - fitting: _not stated_
   - validation: _not stated_
3. **Demonstrate continuum-subtraction artifact with slab model**: Vertically isothermal face-on slab at 40 K with well-mixed dust and gas; gas-to-dust ratio 4 needed to match peak emission  
  > "In order to reproduce the observed peak emission of $^{13}$CO and C$^{18}$O, we had to adopt a gas-to-dust ratio of 4." (On the anti-correlation between dust and molecular line emission)
   - assumption: dust opacity 2.9 cm2/g; abundances from Qi et al. 2011  
  > "a typical dust opacity of 2.9 cm$^2$ g$^{-1}$ at the lines frequencies, and a gas temperature of 40 K" (On the anti-correlation between dust and molecular line emission)
   - fitting: _not stated_
   - validation: _not stated_
4. **Fit radial gas and dust surface density profiles**: RADMC-3D thermal calculation and ray tracing of Gaussian (asymmetric) surface density profiles along north and south azimuths, compared with continuum, integrated and peak CO profiles; second Gaussian added on south gas  
  > "we adopt a different approach and model the gas and dust radial distributions using Gaussian functions centered at the same radius r$_{r}$ and characterized by different widths." (4.2.2 Probing the dust trap hypothesis)
   - software: RADMC-3D, CASA
   - parameter: constant turbulence 0.2 km/s; star 2.4 Msun, 23 Lsun, 6250 K; no dust scattering  
  > "we calculate the line emission adding a constant turbulence velocity of 0.2 km s$^{-1}$ across the disk." (Probing the dust trap hypothesis)
   - assumption: dust and gas share vertical distribution in hydrostatic equilibrium; companion irradiation neglected  
  > "The dust and the gas have the same vertical distribution, which is assumed to be in hydrostatic equilibrium with the midplane temperature." (Comparison with previous models)
   - fitting: best fit parameters with uncertainties in Table 1; fitting algorithm not stated  
  > "Density prescription for the Gaussians describing the dust and gas surface density." (Table 1)
   - validation: comparison with M15 model; scattering test in appendix  
  > "only find minor changes in flux within 5%." (Dust scattering)

## Software

- **CASA** 4.3.1 (v4.3.10 in Software section): calibration, imaging, uvcontsub, smoothing of models  
  > "The data were calibrated using the ALMA pipeline with the version 4.3.1 of CASA." (Observations and data reduction)
- **RADMC-3D** : disk temperature and ray-traced emission models  
  > "The disk temperature is calculated with the radiative code RADMC-3D (cite: Dull2012) assuming thermal equilibrium." (Comparison with previous models)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Dust crescent peak intensity | 0.132 | rms 115 uJy/beam | Jy/beam | 1 | The peak intensity is 0.132 Jy beam$^{-1}$ |
| Total continuum flux density | 3.31 | not stated | Jy | 2 | The total flux density is about 3.31 Jy |
| Systemic velocity | 3.75 | 0.05 | km/s | 2 | we measure a systemic velocity of 3.75 $\pm$ 0.05 km s$^{-1}$ |
| Source c flux density | 0.80 | 6.9 sigma | mJy/beam | 1 | is 0.80 mJy beam$^{-1}$, or 6.9 times the noise level |
| Dust surface density contrast north/south | 54 | not stated | dimensionless | 4 | The density contrast between the dust crescent and the south side at the maximum of the dust surface density is $\sim$ 54. |
| Gas surface density contrast north/south | 3.75 | not stated | dimensionless | 4 | $\Sigma^{north}_{0,g}/\Sigma^{south}_{0,g}= 3.75$ |
| Gas-to-dust ratio at crescent center | 1.7 (north), ~25 (south) | not stated | dimensionless | 4 | the gas-to-dust ratio at $r=r_r$ is 1.7 on the north and about 25 on the south. |
| Total dust mass / gas mass | 1.5e-3 / 5.7e-3 | not stated | Msun | 4 | the total dust mass is 1.5$\times$10$^{-3}$ M$_\odot$ and the total gas mass is 5.7$\times$10$^{-3}$ M$_\odot$. |
| North dust Gaussian peak | 0.65 g/cm2 at 185 AU, widths 28/50 AU | 0.05; 2; 2; 2 | g cm-2; AU | 4 | / Dust     / 0.65 $\pm$ 0.05            / 185 $\pm$ 2 / 28 $\pm$ 2    / 50 $\pm$ 2     / |

## Qualitative findings

- Continuum subtraction removes much of optically thick CO emission, explaining the apparent dust-gas anticorrelation  
  > "This explains the observed anti-correlation between dust and gas in HD 142527, without requiring any chemical or physical effect." (Conclusion)
- Compact continuum and CO source inside cavity at ~50 AU with non-Keplerian kinematics  
  > "We have discovered a compact source of dust continuum and CO emission inside the dust depleted cavity at about 50 AU from the primary star (source $c$)." (Conclusion)

## Claim tuples

- H: Is the dust-CO anticorrelation due to continuum subtraction rather than CO depletion? | E: Slab models and comparison with peak maps with and without continuum subtraction | R: Peak brightness temperature decrement disappears without continuum subtraction; gas T ~40 K | F: Continuum subtraction is the main cause of the apparent anticorrelation | **supported**
- H: Do gas and dust profiles support radial and azimuthal dust trapping? | E: Gaussian profile fits with RADMC-3D | R: Dust narrower than gas, same center; contrasts 54 (dust) and 3.75 (gas); gas-to-dust 1.7 | F: Supports dust trapping in a pressure bump | **supported**
- H: Is there a compact source inside the cavity? | E: Continuum and 13CO moment/spectral analysis | R: 6.9 sigma continuum source at ~50 AU with non-Keplerian gas | F: Possible compact disk around a third companion; needs higher resolution | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: CO freeze-out rejected since gas temperature ~40 K; dust absorption not dominant for optically thick lines; photoevaporation and indirect force vortex scenario disfavored  
  > "our observations suggest a gas temperature of about 40 K in this region, which is a factor of 2 higher than the CO freeze-out temperature." (On the anti-correlation between dust and molecular line emission)
- How they decided it was enough: _not stated_
- Limitation (authors): Global 3D analysis not done; model fails to reproduce secondary maximum on south profile; source c low S/N  
  > "A global 3D analysis of the data is out of the scope of this paper due to its complexity and large computational time." (Derivation of the gas and dust surface density)
- Caveat (inferred, ours): Model fits appear by eye without formal likelihood or MCMC; quoted uncertainties are unclear
- Caveat (inferred, ours): Source c is only ~7 sigma
- Caveat (inferred, ours): 1D profile models with isothermal assumptions and no scattering
- Caveat (inferred, ours): Gas-to-dust ratio depends on assumed opacity and abundances

## Reproducibility

- Data public (paper): ALMA cycle 1 project 2012.1.00725.S; public status not stated  
  > "We obtained ALMA cycle 1 data of the HD 142527 system as part of the project 2012.1.00725.S." (Observations and data reduction)
- Products in archive: _not stated_
- Missing: Line-free channel ranges
- Missing: Model fitting procedure and statistic
- Missing: Mask and clean thresholds
- Missing: Exact RADMC-3D setup (grid, photons)
- Data volume (inferred): ~50-100 GB raw
- Score (inferred): 3/5, Observation and imaging parameters are largely given, but model fitting procedure and several processing details are missing.
- Rediscovery candidate: no, Main results depend on custom radiative transfer model fitting that is not fully specified.

## Links

- Method: (cite: Muto2015) (M15 model and procedure adopted)
- Method: (cite: Dull2012) (RADMC-3D)
- Companion: (cite: Casa2015-2) (previous ALMA/ATCA observations of HD 142527)
- Companion: (cite: Fuka2013) (previous lower-resolution ALMA observations)

## Checks

```json
{
 "quotes": 66,
 "quotes_ok": 66,
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
  "facts": 74,
  "stated": 48,
  "rate": 0.649
 },
 "evidence_ok": true
}
```
