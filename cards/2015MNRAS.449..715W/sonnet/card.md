# Tracing the conversion of gas into stars in Young Massive Cluster Progenitors

`2015MNRAS.449..715W` | Monthly Notices of the Royal Astronomical Society 2015 | first author: Walker, D. L. | arXiv: 1502.03822 | DOI: 10.1093/mnras/stv300

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: milky_way_ism, star_formation
- Question: Are four extreme quiescent Galactic centre clouds gravitationally bound YMC progenitors, and is their gas distribution compact enough to form an Arches-like cluster?  
  > "We derive their masses, dust temperatures and radii and use virial analysis to conclude that they are all likely gravitationally bound – confirming that they are likely YMC progenitors." (abstract)
- Target **G0.253+0.016 (the Brick), clouds d, e, f**: coordinates _not stated_; z/distance ~8.4 kpc  
  > "These HiGAL data cover a wavelength range of 70 – 500 $\mu$m and provide $\sim$ 5.5" or 0.22 pc resolution at the distance of these clouds, which is taken to be $\sim$ 8.4 kpc (cite: distance)." (Results); distance from Reid et al. 2009 (cite: distance)  
  > "These HiGAL data cover a wavelength range of 70 – 500 $\mu$m and provide $\sim$ 5.5" or 0.22 pc resolution at the distance of these clouds, which is taken to be $\sim$ 8.4 kpc (cite: distance)." (Results)

## Data provenance

- ALMA projects: 2011.0.00217.S
- bands: ALMA 3 mm (Cycle 0), used only for G0.253+0.016 density profile  
  > "These data consist of ALMA observations at 3 mm, with an angular resolution of 1.7" (0.07 pc at a distance of 8.4 kpc)." (Discussion)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.7" (0.07 pc)  
  > "These data consist of ALMA observations at 3 mm, with an angular resolution of 1.7" (0.07 pc at a distance of 8.4 kpc)." (Discussion)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: HN13C 1-0 (MALT90, used for line widths) (not stated)
- Other facility **Herschel HiGAL**: Far-IR continuum column density and temperature maps (70-500 um)  
  > "We utilise continuum data from the Herschel infrared Galactic Plane Survey (cite: higal) to measure their global physical properties such as mass, radius and temperature." (Results)
- Other facility **MALT90**: 90 GHz spectral line cubes for kinematics  
  > "The MALT90 survey provides spectral line data for 16 lines in the 90 GHz band." (Results)
- Other facility **BGPS**: 1.1 mm data for Sgr B2 gas profiles  
  > "These data are at a wavelength of 1.1 mm and provide a pixel scale of 7.2” ($\sim$ 0.3 pc at a distance of 8.4 kpc)." (Discussion)
- External data: ALMA Cycle 0 + single-dish (Herschel 500 um) data for G0.253+0.016  
  > "The data were then combined with Herschel 500 $\mu m$ to recover the flux that is filtered out by the interferometric observation." (Discussion) [from Rathborne et al. 2014b (cite: Jill_pdf_2014)]
- External data: UCHII region positions and ZAMS spectral types in Sgr B2  
  > "we first take the positions and zero age main-sequence (ZAMS) spectral classifications of the stellar sources embedded in the Ultra-Compact HII (UCHII) regions from Tables 2 and 3 in (cite: Gaume)." (Discussion) [from Gaume et al. 1995 (cite: Gaume)]
- External data: Arches surface density and cumulative mass profiles  
  > "We utilise the observed surface density profile shown in Figure 16 of (cite: Arches_esp) along with the given best-fit King density profile and parameters" (Discussion) [from Espinoza et al. 2009; Harfst et al. 2010]
- External data: G0.253+0.016 line width and V_LSR  
  > "Coupling these results with L12’s results for G0.253$+$0.016 – V$_{LSR}$ = 36.1 $\pm$ 0.4 km s$^{-1}$, $\Delta$V = 15.1 $\pm$ 1.0 km s$^{-1}$" (Results) [from Longmore et al. 2012 (cite: Brick)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
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
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Molecular tracer categorisation (optically thick/thin/shock tracers)  
  > "We adopt the same categorisation as (cite: Brick_jill), separating these detected molecular transitions as:" (Results) [from (cite: Brick_jill)]
- Dust opacity law from Battersby et al.  
  > "To estimate this, we use the following relation, given in §3.2 of (cite: Cara_higal)" (Discussion) [from (cite: Cara_higal)]
- Gas temperature of 70 K  
  > "assumed to be 70 K in all cases, (cite: Ao_gas_temp)" (Results) [from (cite: Ao_gas_temp)]

### Not stated but needed to reproduce (our reading)

- Coefficient k in the virial mass formula
- ALMA calibration, imaging and feathering details (deferred to Rathborne et al. 2014b)
- Hanning smoothing and CASA fit procedure details for spectra
- How cloud boundaries were drawn on the column-density maps
- Aperture centres and radial bins for profiles

## Analysis recipe

1. **Dust mass and radius from HiGAL**: Sum column density maps above 5e22 cm-2 threshold with mean molecular weight 2.8 mH; effective radius as geometric mean of axes  
  > "we estimate the dust masses of the clouds by assuming a mean molecular weight of 2.8m$_{H}$, multiplying each pixel by its physical area (assuming a distance of 8.4 kpc) and summing over the cloud area." (Dust Mass)
   - parameter: column density threshold 5 x 10^22 cm^-2  
  > "A column density threshold has been applied such that all pixels below 5 x 10$^{22}$ cm$^{-2}$ are masked." (Dust Column Densities & Temperatures)
   - assumption: distance 8.4 kpc  
  > "assuming a distance of 8.4 kpc" (Dust Mass)
   - fitting: _not stated_
   - validation: Mass vs threshold tested (5-10e22 changes mass by 10-40%); compared with Immer et al. and L12  
  > "These estimates agree well with those found by (cite: Immer) and L12." (Dust Mass)
2. **Line widths from MALT90**: Fit cloud-averaged Hanning-smoothed HN13C spectra  
  > "Figure 4 shows Hanning-smoothed HN$^{13}$C spectra that have been averaged over the spatial extent of the clouds" (Gas Velocity Dispersion)
   - software: CASA
   - fitting: _not stated_
   - validation: Emission morphology compared with dust to pick component  
  > "as the morphology of the molecular line emission corresponds to the dust emission well" (Gas Velocity Dispersion)
3. **Virial analysis and timescales**: M_vir = kR dV^2 for uniform sphere, alpha=Mvir/Mdust; sound, crossing and free-fall times  
  > "assuming a uniform spherical density distribution, we use M$_{vir}$ = $k$R$\Delta$V$^{2}$ (cite: virial)" (Virial mass)
   - assumption: gas temperature 70 K, mu=2.8 mH  
  > "$T_{g}$ is the gas temperature (assumed to be 70 K in all cases" (Time-scales)
   - fitting: _not stated_
   - validation: _not stated_
4. **Mass surface density profiles and comparison with Sgr B2 and Arches**: Enclosed mass in circular apertures; BGPS fluxes converted to mass with Kauffmann et al. relation at 20 K; stellar mass from UCHII OB stars with Kroupa IMF correction; SFE factor 1/3  
  > "The dust temperature is assumed to be 20 K" (Discussion)
   - parameter: k_nu = 0.04 cm2 g-1 (nu/505 GHz)^1.75  
  > "k_{\nu} = 0.04 \rm ~ cm^{2} ~ g^{-1} \left(\frac{\nu}{505 ~ GHz}\right)^{1.75}" (Discussion)
   - assumption: gas-to-dust ratio 100  
  > "Note that this contains the explicit assumption that the gas-to-dust ratio is 100." (Discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Fitting HN13C spectra  
  > "where each profile is fitted using the CASA software package (cite: casa)" (Gas Velocity Dispersion)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Dust masses of G0.253, d, e, f | 11.9, 7.6, 11.2, 7.3 x10^4 | systematic factor ~2 | Msun | 1 | We determine the masses of G0.253$+$0.016, ‘d’, ‘e’ and ‘f’ to be 11.9 x 10$^{4}$ M$_{\odot}$, 7.6 x 10$^{4}$ M$_{\odot}$, 11.2 x 10$^{4}$ M$_{\odot}$ and 7.3 x 10$^{4}$ M$_{\odot}$ |
| Effective radii G0.253, d, e, f | 2.9, 3.2, 2.4, 2.0 | not stated | pc | 1 | We derive effective radii of 2.9 pc, 3.2 pc, 2.4 pc and 2.0 pc, respectively |
| HN13C FWHM, cloud d | 16.3 | 1.5 | km/s | 2 | V$_{LSR}$ = 20.75 $\pm$ 0.69 km s$^{-1}$ and $\Delta$V = 16.3 $\pm$ 1.5 km s$^{-1}$ |
| HN13C FWHM, cloud e | 15.51 | 0.52 | km/s | 2 | V$_{LSR}$ = 31.66 $\pm$ 0.22 km s$^{-1}$ and $\Delta$V = 15.51 $\pm$ 0.52 km s$^{-1}$ |
| HN13C FWHM, cloud f | 16.5 | 3.2 | km/s | 2 | V$_{LSR}$ = 40.1 $\pm$ 2.6 km s$^{-1}$ and $\Delta$V = 16.5 $\pm$ 3.2 km s$^{-1}$ |
| Virial ratio alpha for d, e, f | 1.4, 0.7, 0.9 | ~50% | dimensionless | 3 | we compare the dust masses with the virial masses to obtain virial ratios of $\alpha = M_{\rm vir}/M_{\rm dust}=\{1.4,0.7,0.9\}$ |
| Radius enclosing 5e4 Msun (G0.253, d, e, f) | 1.0, 1.2, 0.8, 1.0 | not stated | pc | 1 | 1.0 pc, 1.2 pc, 0.8 pc and 1.0 pc, respectively for G0.253$+$0.016, ‘d’, ‘e’ and ‘f’ |
| Total stellar mass in Sgr B2 from 25 UCHII sources | ~3.5e3 | not stated | Msun | 4 | Taking all 25 sources in (cite: Gaume), we estimate a total stellar mass of $\sim$ 3.5 x 10$^{3}$ M$_{\odot}$. |

## Qualitative findings

- Gas in all four clouds is less centrally concentrated than the Arches stellar distribution  
  > "We again see that G0.253$+$0.016, ‘d’, ‘e’ and ‘f’ are less centrally concentrated than the Arches’ stellar distribution" (Discussion)

## Claim tuples

- H: The clouds are gravitationally bound YMC progenitors | E: Compared virial and dust masses | R: alpha = 1.4, 0.7, 0.9 for d, e, f | F: Clouds are likely bound | **supported**
- H: Gas is compact enough to form an Arches-like cluster directly (scenario i) | E: Compared gas mass profiles with Arches and Sgr B2 | R: Gas is much less centrally concentrated | F: Monolithic collapse disfavoured | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Mass estimates uncertain due to cloud boundary definition and a factor ~2 systematics; gas temperature measured only for G0.253  
  > "We note that these mass estimates are necessarily uncertain due to the ambiguity involved in defining a distinct cloud area" (Dust Mass)
- Caveat (inferred, ours): Gas temperature of 70 K assumed for three clouds without measurement
- Caveat (inferred, ours): Magnetic pressure ignored
- Caveat (inferred, ours): Sgr B2 masses are upper limits
- Caveat (inferred, ours): ALMA data play a minor role

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Virial coefficient k
- Missing: Aperture definitions and profile data
- Missing: ALMA data reduction by earlier paper
- Data volume (inferred): small for HiGAL/MALT90/BGPS maps; ALMA Cycle 0 data tens of GB
- Score (inferred): 3/5, Mostly public survey data and simple calculations, but several parameters are unstated and ALMA is minor.
- Rediscovery candidate: no, Several recipe parameters (virial coefficient, aperture definitions) are not stated and ALMA data are barely used.

## Links

- Method: Battersby et al. 2011 (cite: Cara_higal) (HiGAL column density/temperature maps and dust opacity)
- Companion: Longmore et al. 2012 (cite: Brick) (Analysis of G0.253+0.016 (L12))
- Companion: Rathborne et al. 2014b (cite: Jill_pdf_2014) (ALMA data for G0.253+0.016)
- Related: HiGAL
- Related: MALT90
- Related: BGPS

## Checks

```json
{
 "quotes": 43,
 "quotes_ok": 43,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 29,
  "rate": 0.397
 },
 "evidence_ok": true
}
```
