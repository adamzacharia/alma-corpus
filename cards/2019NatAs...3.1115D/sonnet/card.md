# Molecular clouds in the Cosmic Snake normal star-forming galaxy 8 billion years ago

`2019NatAs...3.1115D` | Nature Astronomy 2019 | first author: Dessauges-Zavadsky, Miroslava | arXiv: 1909.08010 | DOI: 10.1038/s41550-019-0874-0

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, star_formation
- Question: Does a typical Milky Way progenitor at z = 1.036 host giant molecular clouds, and how do their properties compare with local GMCs?  
  > "Here we search for GMCs in a typical Milky Way progenitor at z = 1.036." (abstract)
- Target **Cosmic Snake (lensed by MACS J1206.2–0847)**: coordinates RA = +12h 06min 10.76s, Dec = −08° 48′ 04.80″  
  > "The field of view was centred at RA = +12h 06min 10.76s and Dec = −08° 48′ 04.80″." (Observations, data reduction and imaging); "typical Milky Way progenitor at z = 1.036" (abstract); z/distance z = 1.036  
  > "The field of view was centred at RA = +12h 06min 10.76s and Dec = −08° 48′ 04.80″." (Observations, data reduction and imaging); "typical Milky Way progenitor at z = 1.036" (abstract); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.01330.S
- bands: Band 6, CO(4–3) at 226.44 GHz  
  > "Onsource integration time of 52.3 minutes was obtained in band 6 with 38 12m antennae in the extended C38-5 configuration" (Observations, data reduction and imaging)
- frequencies and spectral setup: SPW2 7.8125 MHz resolution (~10.343 km/s) at 226.44 GHz; three other 1.875 GHz SPWs for continuum  
  > "The spectral window 2, with a spectral resolution set to 7.8125MHz (~10.343kms [−1] ), was tuned at 226.44 GHz, the redshifted CO(4–3) line" (Observations, data reduction and imaging)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C38-5, 38 12m antennae  
  > "with 38 12m antennae in the extended C38-5 configuration, with maximum and minimum baselines of 1.6km and 47m, respectively." (Observations, data reduction and imaging)
- baselines: 47 m to 1.6 km  
  > "with maximum and minimum baselines of 1.6km and 47m, respectively." (Observations, data reduction and imaging)
- angular resolution: 0.22″ × 0.18″, PA +85°  
  > "has a synthesized beam size of 0.22″ × 0.18″ at the position angle of +85°" (Observations, data reduction and imaging)
- max recoverable scale: 3.4″  
  > "The maximum recoverable scale of the observations, θ MRS = 3.4″" (Observations, data reduction and imaging)
- sensitivity: 0.29 mJy/beam per 10.343 km/s channel  
  > "an RMS of 0.29mJybeam [−1] per 10.343kms [−1] channel" (Observations, data reduction and imaging)
- time on source: 52.3 minutes  
  > "Onsource integration time of 52.3 minutes was obtained in" (Observations, data reduction and imaging)
- observing dates: data delivered August 2015  
  > "ALMA observations of the Cosmic Snake arc were delivered in August 2015." (Observations, data reduction and imaging)
- pi or archival as stated: _not stated_
- Line: CO J=4–3 (not stated (observed at 226.44 GHz, z=1.036))
- Other facility **IRAM PdBI**: CO(2–1) data used to derive r4,2 luminosity ratio  
  > "The frequency was tuned at 113.23GHz, the redshifted frequency of the CO(2–1) line." (Observations, data reduction and imaging)
- Other facility **HST (CLASH)**: 16-band images for stellar mass radial profile; stellar clumps  
  > "We extracted the aperture-corrected photometry in the 16 HST bands, available through the Cluster Lensing and Supernovae survey with HST (CLASH" (Galactic shear, tides and hydrostatic pressure)
- External data: Tailored lens model of MACS J1206 and stellar clump masses  
  > "The tailored lens model of the cluster, refined to match the arc in the image plane, was published in ref. [7] and is adopted here." (Methods) [from Cava et al. 2018 (cite: ref 7)]
- External data: Local GMC and SDP81 comparison samples  
  > "local quiescent galaxies (filled grey histogram [1][,][17][–][20] )" (Figure 2 caption) [from refs 1, 2, 17–20, 22, 23]
- External data: CO excitation r2,1 from z~1.5 BzK galaxies  
  > "extrapolated from r4,2 measured in the Cosmic Snake galaxy and r 2,1 reported in z ~1.5 BzK galaxies [33]" (Methods) [from Daddi et al. 2015 (cite: ref 33)]
- Simulation/model as data: CASA simobserve simulations of smooth exponential disk vs clumpy disk lensed with Lenstool  
  > "we performed CASA visibility simulations with the ‘simobserve’ routine" (Molecular cloud identification)

## Processing

### Calibration

- pipeline or manual: CASA pipeline plus careful flagging  
  > "A careful flagging of the pipeline-calibrated visibilities yielded an improvement of ~10% in the final RMS." (Observations, data reduction and imaging)
- casa version: CASA 4.2.2  
  > "package, version 4.2.2." (Observations, data reduction and imaging)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: 3C273 flux; J1216–1033 and J1256–0547 bandpass and phase  
  > "3C273 was selected as flux calibrator, while J1216–1033 and J1256–0547 were used for bandpass and phase calibrations." (Observations, data reduction and imaging)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA clean, interactive  
  > "while interactively cleaning all channels with the ‘clean’ routine in CASA, using a custom mask, until convergence." (Observations, data reduction and imaging)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "performed with Briggs weighting and robust factor of 0.5" (Observations, data reduction and imaging)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: custom mask  
  > "using a custom mask, until convergence." (Observations, data reduction and imaging)
- multiscale scales: _not stated_
- continuum subtraction: 1 mm continuum imaged from line-free channels and subtracted in visibilities  
  > "The detected 1 mm continuum was then subtracted from CO(4–3) spectral line visibilities." (Observations, data reduction and imaging)
- line free channels: _not stated_
- primary beam correction: applied after cleaning  
  > "Finally, we performed the primary beam correction." (Observations, data reduction and imaging)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.22″ × 0.18″, PA +85°  
  > "synthesized beam size of 0.22″ × 0.18″ at the position angle of +85°" (Observations, data reduction and imaging)
- final rms: 0.29 mJy/beam per 10.343 km/s channel  
  > "an RMS of 0.29mJybeam [−1] per 10.343kms [−1] channel" (Observations, data reduction and imaging)

### Inherited from earlier work

- Lens model adopted from earlier paper  
  > "was published in ref. [7] and is adopted here." (Methods) [from Cava et al. 2018 (cite: ref 7)]
- _not stated_ [from Leroy et al. 2015 (cite: ref 23)]
- Internal pressure formula  
  > "We estimated the internal kinetic pressure" (Methods, Molecular cloud physical properties) [from Hughes et al. 2013 (cite: ref 6)]
- Star formation efficiency definition  
  > "efficiency of star formation of the galaxy" (Methods) [from Evans et al. 2009 (cite: ref 27)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges for continuum subtraction
- Clean threshold, cell size and image size
- Exact aperture definitions per channel
- Lens model files and magnification maps
- Ellipse-fitting details for 4σ contour radii
- Rest frequency of CO(4–3) used

## Analysis recipe

1. **image CO(4–3) cube and moment maps**: Pipeline calibration, flagging, continuum subtraction, Briggs clean, primary beam correction; immoments for moments with 3σ threshold  
  > "Moment maps of the CO(4–3) emission were obtained using the ‘immoments’ routine in CASA" (Observations, data reduction and imaging)
   - software: CASA
   - parameter: robust = 0.5; 10.343 km/s channels  
  > "performed with Briggs weighting and robust factor of 0.5" (Observations, data reduction and imaging)
   - fitting: _not stated_
   - validation: MRS 3.4″ comparable to source size; r4,2 suggests no flux lost  
  > "We are thus confident that we recovered all the expected sizes of the CO(4–3) emission, and no large-scale structure was filtered out." (Observations, data reduction and imaging)
2. **identify molecular clouds**: Fidelity-based detection in 26 channel maps (≥6σ per channel or ≥4σ in two adjacent channels), cross-matching counter-images with lens model  
  > "We thus also extracted all ≥4 σ emissions co-spatial in two adjacent channel maps." (Molecular cloud identification)
   - software: Lenstool
   - parameter: 100% fidelity at S/N=6.3 per channel; 5.7σ for two channels  
  > "In individual channel maps, the fidelity of 100% is reached at S / N = 6.3." (Molecular cloud identification)
   - fitting: _not stated_
   - validation: simobserve simulations show clumps, not smooth disk, are detected  
  > "only when this total flux is distributed in clumps do we detect the corresponding clump emissions" (Molecular cloud identification)
3. **derive gas masses, radii, velocity dispersions**: Lensing-corrected fluxes in custom apertures; mass from L'CO(4-3) with r41=0.33 and alpha_CO=4.36; FWHM radii beam-deconvolved; sigma_v from moment map and Gaussian fit  
  > "We used two approaches to determine the velocity dispersion of a given counter-image." (Molecular cloud physical properties)
   - software: CASA
   - assumption: Milky Way alpha_CO = 4.36 incl. helium; r4,1 = 0.33  
  > "Milky Way CO-to-H 2 conversion factor of 4 : 36 M ⊙ (K km s [−1] pc [2] ) [−1], which includes the correction factor of 1.36 for helium." (Supplementary Table 1)
   - fitting: Gaussian fit to spectrum  
  > "Second, we extracted the integrated CO(4–3) line spectrum of that counter-image, and measured the line FWHM by fitting a Gaussian function." (Methods, Molecular cloud physical properties)
   - validation: values from different counter-images agree within factor 2  
  > "agree within better than a factor of 2" (Molecular cloud physical properties)
4. **virial analysis and alpha_CO**: Virial mass for spherical 1/r profile; 14 virialized clouds give mean alpha_CO  
  > "assumption that GMCs are spherical and have a density profile inversely proportional to radius" (Molecular cloud physical properties)
   - fitting: _not stated_
   - validation: _not stated_
5. **pressure, Mach number, shear, tides, hydrostatic pressure**: Internal pressure, Mach number with cs=0.45 km/s (35 K); stellar mass profile via Hyperz in 20 ellipses; rotation curve, shear, tides  
  > "where the sound speed c s = 0.45kms [−1] was calculated for molecular hydrogen at 35K" (Methods)
   - software: Hyperz
   - assumption: Thin axisymmetric disk, Salpeter IMF, solar metallicity, exponentially declining SFH  
  > "We adopted the Salpeter initial mass function [43]." (Methods)
   - fitting: SED fitting  
  > "using the updated version of the Hyperz fitting code for photometric redshift and spectral energy distribution [39]" (Methods, Galactic shear, tides and hydrostatic pressure)
   - validation: _not stated_

## Software

- **CASA** 4.2.2: pipeline, clean, immoments, simobserve  
  > "Common Astronomy Software Application (CASA [32] ) package, version 4.2.2." (Observations, data reduction and imaging)
- **GILDAS (CLIC, MAPPING)** : PdBI CO(2–1) reduction  
  > "Standard data reduction was performed using the GILDAS software packages CLIC and MAPPING." (Observations, data reduction and imaging)
- **Lenstool** : lens model and magnifications, MCMC uncertainties  
  > "The lens model was obtained using Lenstool" (Code availability)
- **Hyperz** : SED fitting of stellar masses  
  > "The spectral energy distribution fitting was performed with a modified version of the Hyperz code" (Code availability)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of molecular clouds | 17 | not stated | dimensionless | 2 | We identify 17 molecular clouds |
| Median GMC gas mass | 5.8e7 | not stated | Msun | 3 | The median mass of 5.8 × 10 [7] M ⊙ is two orders of magnitude higher |
| Median surface density | 2600 | not stated | Msun pc^-2 | 3 | with a median value of 2,600 M ⊙ pc [−2] |
| Total CO(4–3) flux | 5.2 | 0.4 | Jy km/s | 1 | (5.2 ± 0.4)Jykms [−1] |
| r4,2 | 0.41 | 0.08 | dimensionless | 1 | = 0.41±0.08 |
| Mean alpha_CO | 3.8 | 1.1 | Msun (K km/s pc^2)^-1 | 4 | We derive a mean CO-to-H 2 conversion factor of 3.8 ± 1.1 |
| Median Mach number | 80 | 13 | dimensionless | 5 | We obtained a median Mach number of 80 ± 13 |
| Hydrostatic pressure | ~10^7.7 | not stated | cm^-3 K | 5 | We obtained the hydrostatic pressure of ~10 [7.7] cm [−3] K |

## Qualitative findings

- GMCs lie offset from Larson relations and resemble local starburst GMCs  
  > "The molecular clouds hosted in high-redshift galaxies turn out to be offset from the Larson scaling relations" (main text)

## Claim tuples

- H: Do GMCs in a normal z~1 galaxy resemble local GMCs? | E: Lensed ALMA CO(4–3) cloud identification and property measurement | R: Masses, surface densities and velocity dispersions 10–100 times local | F: GMC properties are not universal and inherit ambient ISM conditions | **supported**
- H: Are the GMCs virialized and what is alpha_CO? | E: Virial masses vs CO luminosity | R: 14 of 17 within factor 3; alpha_CO 3.8±1.1 | F: Milky Way-like conversion factor | **supported**
- H: Do GMCs relate to stellar clumps by disk fragmentation? | E: Compare gas and stellar clump masses | R: Similar masses; SFE ~26–34% | F: Supports fragmentation formation | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Briggs robust 0.5 gives good resolution–sensitivity trade-off  
  > "gave a good trade-off between resolution and sensitivity" (Observations, data reduction and imaging)
- Alternative: Smooth exponential disk would appear clumpy due to lensing/interferometry; simulations reject it  
  > "could appear artificially clumpy due to lensing and interferometric effects [35]" (Molecular cloud identification)
- How they decided it was enough: _not stated_
- Limitation (authors): Projection effects/blends may inflate masses and radii; values may be upper limits  
  > "we should keep in mind they may still be upper limits." (Molecular cloud physical properties)
- Caveat (inferred, ours): Single galaxy; clouds may be associations blended along line of sight
- Caveat (inferred, ours): alpha_CO derived from virial assumption that is itself being tested
- Caveat (inferred, ours): Lens model uncertainties propagate to sizes
- Caveat (inferred, ours): r41 extrapolated from r42

## Reproducibility

- Data public (paper): ALMA raw data in archive; HST CLASH public; other data on request  
  > "The ALMA raw data of the Cosmic Snake arc are available through the ALMA archive under the project identification 2013.1.01330.S." (Data availability)
- Products in archive: _not stated_
- Code: Standard public codes only; no custom code released  
  > "The lens model was obtained using Lenstool, publicly available" (Code availability)
- Missing: Lens model
- Missing: Aperture definitions
- Missing: Clean parameters
- Missing: PdBI data
- Data volume (inferred): ~10–30 GB raw for one ALMA band 6 execution set
- Score (inferred): 3/5, Public data and many steps described, but lens model, apertures and cloud extraction are manual and not fully specified.
- Rediscovery candidate: no, Data public, but cloud identification relies on lens model and custom manual apertures.

## Links

- Method: Walter et al. 2016 (cite: ref 34) (Fidelity definition)
- Method: Jullo et al. 2007 (cite: ref 31) (Lenstool)
- Companion: Cava et al. 2018 (cite: ref 7) (Lens model and stellar clumps)
- Companion: Patrício et al. 2018 (cite: ref 13) (Kinematics of the galaxy)
- Related: CLASH

## Checks

```json
{
 "quotes": 71,
 "quotes_ok": 71,
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
  "facts": 80,
  "stated": 55,
  "rate": 0.688
 },
 "evidence_ok": true
}
```
