# ALMA observation of the disruption of molecular gas in M87

`2018MNRAS.475.3004S` | Monthly Notices of the Royal Astronomical Society 2018 | first author: Simionescu, A. | arXiv: 1801.01264 | DOI: 10.1093/mnras/sty047

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: galaxy_clusters_and_sz, agn_and_quasars
- Question: Is there molecular gas (CO 2-1) in the M87 filament southeast of the nucleus, and how does it relate to the AGN radio lobe and shock?  
  > "Here, we present new Atacama Large Millimeter Array (ALMA) observations of the coldest, molecular gas phase at the location of these filaments that were previously detected at other wavelengths." (Introduction)
- Target **M87 southeast filament**: coordinates ~40" southeast of the M87 AGN (no coordinates given)  
  > "we assume a systemic velocity of M87 of $v = 1307$ km s$^{-1}$, a redshift z=0.00436, and a luminosity distance $D_L=16.1$ Mpc (cite: blakeslee2009)" (Observations and data analysis); z/distance z=0.00436, D_L=16.1 Mpc  
  > "we assume a systemic velocity of M87 of $v = 1307$ km s$^{-1}$, a redshift z=0.00436, and a luminosity distance $D_L=16.1$ Mpc (cite: blakeslee2009)" (Observations and data analysis); distance from Blakeslee et al. 2009  
  > "we assume a systemic velocity of M87 of $v = 1307$ km s$^{-1}$, a redshift z=0.00436, and a luminosity distance $D_L=16.1$ Mpc (cite: blakeslee2009)" (Observations and data analysis)

## Data provenance

- ALMA projects: 2013.1.00862.S
- bands: Band 6  
  > "which falls within the sensitivity range of ALMA’s Band 6 receivers (211 – 275 GHz)" (Observations and data analysis)
- frequencies and spectral setup: One baseband on CO(2-1) at 229.5 GHz, three for continuum  
  > "One baseband was centered on the CO(2–1) line, while the other three sampled the local continuum." (Observations and data analysis)
- continuum bandwidth: _not stated_
- arrays: 12m antennae, 34-41 operational  
  > "Between 34 and 41 of the 12m antennae were operational." (Observations and data analysis)
- configurations: _not stated_
- baselines: maximum 350 m  
  > "The maximum baselines extended to 350 m" (Observations and data analysis)
- angular resolution: 0.7"  
  > "delivering a minimum angular resolution of 0.7$^{\prime\prime}$" (Observations and data analysis)
- max recoverable scale: ~10"  
  > "largest recoverable angular scale of $\sim$10$^{\prime\prime}$and a primary beam (field of view, FOV) of 28$^{\prime\prime}$" (Observations and data analysis)
- sensitivity: 0.2 mJy/beam per 50 km/s channel  
  > "RMS noise of 0.2 mJy per beam per 50 km s$^{-1}$ channel" (Observations and data analysis)
- time on source: 5.4 h total, 3 h on source  
  > "The total observing time was 5.4 hours, of which 3 on source and 2.4 on calibrators." (Observations and data analysis)
- observing dates: 2014 Dec 11 to 2015 Jan 3, 4 scheduling blocks  
  > "over 4 separate scheduling blocks executed between 2014 December 11 and 2015 January 3" (Observations and data analysis)
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (229.5 GHz (at M87 redshift))
- Other facility **VLA 6 cm**: radio lobe image for comparison  
  > "the 6 cm VLA image" (abstract)
- Other facility **HST WFPC2 F660N**: Halpha fluxes of two regions  
  > "Using the HST Wide Field and Planetary Camera 2 (WFPC2) F660N data, we obtain comparable H$\alpha$ fluxes for the two regions" (Results)
- Other facility **Chandra**: X-ray filament and shock/pressure maps (from literature)  
  > "the soft X-ray (0.7–0.9 keV) Chandra image is known to reveal a very similar filament morphology (cite: werner2010)" (Results)
- Other facility **Herschel PACS**: [CII] velocities for comparison  
  > "while \[C ii\] measurements give $v=-123\pm5$ km s$^{-1}$ and $\sigma\sim55$ km s$^{-1}$ (cite: werner2013)" (Results)
- External data: Shock pressure map and Mach number >=1.2 from Chandra  
  > "report the presence of a shock with a Mach number of at least 1.2, driven by the expansion of the 6 cm radio lobe" (Results) [from (cite: million2010b)]
- External data: CO(2-1) to CO(1-0) flux density ratio of 3.2  
  > "a CO(2–1) to CO(1–0) flux density ratio of 3.2 (cite: david2014)" (Results) [from (cite: david2014)]
- External data: [CII] velocity and dispersion, [OIII]/Hbeta ratios  
  > "the \[O iii\]/H$\beta$ emission line ratios reported by (cite: werner2013) show a strong decrease with radius" (Results) [from (cite: werner2013)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.3.1  
  > "The data were reduced using version 4.3.1 of the Common Astronomy Software Applications (CASA) software package" (Observations and data analysis)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Ganymede and Callisto (flux); quasars 3C 273, J1058+0133, J1229+0203  
  > "Ganymede and Callisto, along with Quasars 3C 273, J1058+0133, and J1229+0203 were used for amplitude, flux, and phase calibration." (Observations and data analysis)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0  
  > "Measurement sets were imaged using Briggs weighting with a robust parameter of 0" (Observations and data analysis)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub using line-free channels  
  > "The continuum was subtracted by summing all line-free channels and removing the emission using the task `uvcontsub`." (Observations and data analysis)
- line free channels: _not stated_
- primary beam correction: applied to all images  
  > "All ALMA images presented in this paper have been corrected for response of the primary beam." (Observations and data analysis)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 1.4" x 0.7", PA 75 deg  
  > "yielding a beamsize of 1.4$^{\prime\prime}$$\times$ 0.7$^{\prime\prime}$ at a position angle of 75 degrees" (Observations and data analysis)
- final rms: 0.2 mJy/beam per 50 km/s channel  
  > "The final continuum-subtracted CO(2–1) data cube has an RMS noise of 0.2 mJy per beam per 50 km s$^{-1}$ channel." (Observations and data analysis)

### Inherited from earlier work

- Masked moment technique for moment maps  
  > "We have further employed the “masked moment” technique described by (cite: dame2011)" (Results) [from (cite: dame2011)]
- Systemic velocity, redshift and distance assumed for consistency with Herschel-PACS  
  > "For consistency with the Herschel-PACS results (cite: werner2013), we assume a systemic velocity of M87 of $v = 1307$ km s$^{-1}$" (Observations and data analysis) [from (cite: werner2013)]

### Not stated but needed to reproduce (our reading)

- Image size, cell size, deconvolver, cleaning threshold and mask
- Line-free channel ranges for uvcontsub
- Spectral window/channel setup details and rest frequency used
- Whether the pipeline or manual calibration was used and flux scale uncertainty
- Details of the masked-moment parameters (smoothing kernel) and the flux integration aperture
- How flux error was derived
- Details of HST Halpha reduction, [NII] and stellar light subtraction
- Pointing coordinates of the ALMA field

## Analysis recipe

1. **Reduce data and image CO(2-1) cube**: CASA reduction, uvcontsub, Briggs imaging, primary beam correction  
  > "The continuum was subtracted by summing all line-free channels and removing the emission using the task `uvcontsub`." (Observations and data analysis)
   - software: CASA
   - parameter: robust = 0  
  > "Briggs weighting with a robust parameter of 0" (Observations and data analysis)
   - fitting: _not stated_
   - validation: _not stated_
2. **Masked-moment velocity and dispersion maps**: 3D mask in position-velocity space on 10 km/s binned cube, keeping >3 sigma detections  
  > "Applying this analysis to a data cube binned to 10 km s$^{-1}$ channels, and keeping only the regions where the CO(2–1) line was detected with a significance above $3\sigma$" (Results)
   - software: makeplots (Davis)
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive molecular gas mass**: Mass formula from CO(2-1) integral with Galactic XCO and CO(2-1)/(1-0) ratio  
  > "Assuming the average Milky Way value of $X_{\rm CO} = 2\times10^{20} \frac{\rm cm^{-2}}{\rm K\: km\: s^{-1}}$ (cite: solomon1987) and a CO(2–1) to CO(1–0) flux density ratio of 3.2 (cite: david2014)" (Results)
   - assumption: XCO = 2e20 cm^-2/(K km/s); ratio 3.2; D_L = 16.1 Mpc; z=0.00436  
  > "Assuming the average Milky Way value of $X_{\rm CO} = 2\times10^{20} \frac{\rm cm^{-2}}{\rm K\: km\: s^{-1}}$ (cite: solomon1987)" (Results)
   - fitting: _not stated_
   - validation: Caveat that XCO is not universal  
  > "Note however that this value is subject to significant systematic uncertainty, as the Galactic conversion factor is not expected or observed to be universal (cite: bolatto2013)." (Results)
4. **Compare CO and Halpha inside vs outside radio lobe**: Two 9x9" regions; HST F660N Halpha fluxes; CO 3 sigma upper limit inside  
  > "we consider two square regions, each with a size of $9\times9$$^{\prime\prime}$  as shown in Figure [3](#matrix)." (Results)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.3.1: data reduction and imaging  
  > "The data were reduced using version 4.3.1 of the Common Astronomy Software Applications (CASA) software package" (Observations and data analysis)
- **uvcontsub** : continuum subtraction  
  > "removing the emission using the task `uvcontsub`" (Observations and data analysis)
- **makeplots (T. Davis)** : masked moment analysis code  
  > "the code implementing this is publicly available from Timothy Davis at https://github.com/TimothyADavis/makeplots" (Results)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO(2-1) total flux | 5.5e-18 | 0.6e-18 | erg s^-1 cm^-2 | 3 | The total flux measured in the CO(2–1) line is $(5.5 \pm 0.6) \times 10^{-18}$ erg s$^{-1}$ cm$^{-2}$ |
| Emission integral S_CO dv | 0.56 | 0.06 | Jy km/s | 3 | $S_{\rm CO}\Delta\nu = 0.56 \pm 0.06$ Jy km s$^{-1}$ is the emission integral |
| Molecular gas mass | 4.7e5 | 0.4e5 | Msun | 3 | $M_{\rm H_2}=(4.7 \pm 0.4) \times 10^5 M_\odot$ |
| LOS velocity | -129 | 3 | km/s | 2 | line-of-sight (LOS) velocity of $v=-129\pm3$ km s$^{-1}$ |
| Velocity dispersion | 27 | 3 | km/s | 2 | a narrow line width, $\sigma=27\pm3$ km s$^{-1}$ |
| CO(2-1) 3 sigma upper limit, inner region | 1.3e-18 | not stated | erg s^-1 cm^-2 | 4 | the $3\sigma$ upper limit on the CO(2–1) flux from the inner region is $1.3\times10^{-18}$ erg s$^{-1}$ cm$^{-2}$ |
| Halpha flux inner region | 3.1e-14 | 0.3e-14 | erg s^-1 cm^-2 | 4 | $(3.1\pm0.3) \times10^{-14}$ and $(2.5\pm0.2) \times 10^{-14}$ erg s$^{-1}$ cm$^{-2}$ nearer and further from the AGN, respectively |
| Halpha flux outer region | 2.5e-14 | 0.2e-14 | erg s^-1 cm^-2 | 4 | $(3.1\pm0.3) \times10^{-14}$ and $(2.5\pm0.2) \times 10^{-14}$ erg s$^{-1}$ cm$^{-2}$ nearer and further from the AGN, respectively |
| Time since shock passage (estimate) | 1.1 | not stated | Myr | 0 | we estimate that in this scenario 1.1 Myr have elapsed between the shock passage and the observed destruction of the molecular gas |

## Qualitative findings

- CO emission lies only outside the 6 cm radio lobe but inside the X-ray shock, while Halpha is present on both sides.  
  > "CO emission is *only* observed outside of the radio lobe." (Results)
- M87 is cold-gas poor given its Halpha flux compared with other cluster central galaxies.  
  > "M87 indeed appears very cold-gas poor given the H$\alpha$ flux measurements presented here." (Results)

## Claim tuples

- H: Is molecular gas detectable in the M87 filament? | E: ALMA Band 6 CO(2-1) observation of the field 40" SE of the nucleus | R: Flux (5.5±0.6)e-18 erg/s/cm2, M_H2 = (4.7±0.4)e5 Msun | F: First secure detection of molecular gas in M87 | **supported**
- H: Does the AGN radio lobe or shock affect the molecular gas? | E: Compare CO and Halpha inside and outside the radio lobe | R: Halpha/CO ratio changes by factor >5 across the lobe edge | F: AGN lobe or shock destroys or excites the molecular gas | **partially**
- H: Is the molecular gas dynamically quiescent? | E: Masked moment velocity dispersion map | R: sigma = 27±3 km/s, an order of magnitude below the [CII] velocity gradient | F: Predominantly laminar dynamics | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Coincidence of X-ray shock with CO dimming in 3D judged unlikely; a time lag after shock passage remains possible.  
  > "We conclude that it is unlikely that the X-ray shock coincides in 3D geometry with the dimming of CO(2–1) emission observed with ALMA." (Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Mass is subject to large systematic uncertainty from the assumed Galactic XCO.  
  > "albeit with large uncertainties related to the assumption that the CO-to-H$_2$ conversion factor is similar to that in our own Galaxy" (Conclusions)
- Caveat (inferred, ours): Single pointing covers only a small part of the filament
- Caveat (inferred, ours): Interpretation (lobe vs shock) depends on poorly known 3D geometry
- Caveat (inferred, ours): Flux errors and the CO(2-1)/(1-0) ratio assumption are weakly justified
- Caveat (inferred, ours): Only an upper limit inside the lobe, with no search for higher-J lines

## Reproducibility

- Data public (paper): ALMA project cited in acknowledgments; archive data  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00862.S." (Acknowledgments)
- Products in archive: _not stated_
- Code: Masked-moment code is public (Davis makeplots)  
  > "the code implementing this is publicly available from Timothy Davis at https://github.com/TimothyADavis/makeplots" (Results)
- Missing: Imaging parameters (cell, size, mask, threshold)
- Missing: Line-free channel selection
- Missing: Flux aperture and error derivation
- Missing: HST and VLA/Chandra reduction details
- Data volume (inferred): ~10-50 GB raw (4 execution blocks, Band 6)
- Score (inferred): 3/5, Public data and main recipe are simple, but imaging and flux extraction details are missing.
- Rediscovery candidate: yes, Public data; CO flux, mass, velocity and dispersion are numeric and the recipe is short, though imaging details are missing.

## Links

- Method: (cite: dame2011) (masked moment technique)
- Method: (cite: mcmullin2007) (CASA)
- Companion: (cite: werner2013) (Herschel [CII] and [OIII] study of the same filament)
- Companion: (cite: million2010b) (Chandra shock and thermodynamic maps)

## Checks

```json
{
 "quotes": 60,
 "quotes_ok": 60,
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
  "stated": 45,
  "rate": 0.608
 },
 "evidence_ok": true
}
```
