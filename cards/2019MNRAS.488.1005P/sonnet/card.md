# Upper limits on protolunar disc masses using ALMA observations of directly imaged exoplanets

`2019MNRAS.488.1005P` | Monthly Notices of the Royal Astronomical Society 2019 | first author: Pérez, Sebastián | arXiv: 1906.11774 | DOI: 10.1093/mnras/stz1775

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: exoplanets, protoplanetary_disks
- Question: How much circumplanetary (protolunar) dust surrounds young directly-imaged exoplanets, and is it enough to form regular satellite systems (~1e-4 Mp)?  
  > "Is this relation a common trait for gas giant exoplanetary systems?" (Introduction); "These allow for upper limits on the amount of circumplanetary dust to be derived from detailed radiative transfer models." (abstract)
- Target **PZ Tel b**: coordinates _not stated_; z/distance 47 pc  
  > "| PZ Tel b       | 21             | 47             | 1.0" (Table 1); distance from GAIA Data Release 2  
  > "| PZ Tel b       | 21             | 47             | 1.0" (Table 1)
- Target **51 Eri b**: coordinates _not stated_; z/distance 30 pc  
  > "| 51 Eri b       | 21             | 30             | 1.75" (Table 1); distance from GAIA Data Release 2  
  > "| 51 Eri b       | 21             | 30             | 1.75" (Table 1)
- Target **AB Pic b**: coordinates _not stated_; z/distance 50 pc  
  > "| AB Pic b       | 30             | 50             | 0.8" (Table 1); distance from GAIA Data Release 2  
  > "| AB Pic b       | 30             | 50             | 0.8" (Table 1)
- Target **kappa And b**: coordinates _not stated_; z/distance 50 pc  
  > "| $\kappa$ And b | 47             | 50             | 2.5" (Table 1); distance from GAIA Data Release 2  
  > "| $\kappa$ And b | 47             | 50             | 2.5" (Table 1)

## Data provenance

- ALMA projects: 2015.1.01210.S, 2016.1.00358.S
- bands: 1.3 mm  
  > "We obtained observations at 1.3 millimeter wavelength using the 12m array" (2 Data description)
- frequencies and spectral setup: Three 2.0 GHz continuum spws centred at 232.469, 217.871, 215.371 GHz; a fourth spw at 230.507 GHz for 12CO (1.875 GHz, 960 channels); FDM  
  > "Three spectral windows with 2.0 GHz bandwidth were set up for detecting the dust continuum, centred at 232.469, 217.871, and 215.371 GHz respectively." (2 Data description)
- continuum bandwidth: _not stated_
- arrays: 12m array  
  > "using the 12m array with baselines ranging from 19 metres to up to 3.0 kilometres" (2 Data description)
- configurations: _not stated_
- baselines: 19 m to 3.0 km  
  > "baselines ranging from 19 metres to up to 3.0 kilometres" (2 Data description)
- angular resolution: ~0.15" (natural weights)  
  > "resulting in an angular resolution of $\sim$0.15$''$ (using natural weights)" (2 Data description)
- max recoverable scale: ~2.0"  
  > "sensitive to spatial scales of up $\sim$2.0$''$" (2 Data description)
- sensitivity: 3 sigma limits 78-180 uJy (PZ Tel 84, 51 Eri 81, AB Pic 78, kappa And 180)  
  > "| PZ Tel b       | 21             | 47             | 1.0                    | 1.32                  | 5250           | 25             | 38                        | 0.25                    | 2700                               | 84" (Table 1)
- time on source: ~38 min per observing block including calibrations  
  > "each observing block was integrated for $\sim$38 minutes in total (including calibrations)" (2 Data description)
- observing dates: Cycles 3 and 4  
  > "These observations were performed during Cycles 3 and 4" (2 Data description)
- pi or archival as stated: _not stated_
- Line: 12CO not stated (230.507 GHz (spw centre))
- Other facility **GAIA DR2**: Distances  
  > "$\dagger$ GAIA Data Release 2." (Table 1)
- External data: Stellar and planet parameters (mass, radius, temperature, age, semi-major axis) for the sample  
  > "Planet temperatures are constrained from observations assuming a hot start model." (Table 1) [from refs 1-26 in Table 1 (e.g. (cite: Maire2016), (cite: Macintosh2015))]
- External data: Previous ALMA non-detections of young companions used for comparison (HR 8799, DH Tau, CT Cha, GSC6214-210, 1RXS1609, GQ Lup, 2M1207, beta Pic, HD 95086)  
  > "Previous 1.3 mm observations from (cite: Booth2016)" (Table 1) [from (cite: Booth2016); (cite: Wu2017); (cite: Ricci2017b); (cite: Matra2019); (cite: Su2017)]

## Processing

### Calibration

- pipeline or manual: ALMA Pipeline in CASA, run by ALMA staff  
  > "All data were calibrated by the ALMA staff using the ALMA Pipeline in the CASA package" (2 Data description)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA v.5.2 tclean (CLEAN)  
  > "Image reconstruction was performed using the CLEAN algorithm (CASA v.5.2, task `tclean`) with ‘natural’ weights." (2 Data description)
- deconvolver: _not stated_
- weighting robust: natural  
  > "with ‘natural’ weights" (2 Data description)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: All spectral windows combined in imaging; multiple observing blocks concatenated with proper motions accounted for  
  > "All spectral windows were combined in the imaging." (2 Data description)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: RMS from CLEANed images, reported in table  
  > "The RMS value for each dataset was calculated from the CLEANed images" (2 Data description)

### Inherited from earlier work

- Disc truncation radius 0.4 R_Hill for fiducial model  
  > "We used a power-law slope of $-1$ and an exponential cutoff radius $r_{\rm c}$ of 0.4 times the planet’s Hill radius ($R_{\rm H}$) as our fiducial model (cite: AyliffeBate2009)." (3 CPD models) [from (cite: AyliffeBate2009)]
- Collisional dust evolution model  
  > "we used the model presented in (cite: Marino2017)" (4.2 Collisional evolution) [from (cite: Marino2017)]
- beta Pic b RMS and limit taken from earlier ALMA analysis  
  > "there is no point-like emission above 3$\sigma$ (cite: Matra2019)" (3 CPD models) [from (cite: Matra2019)]

### Not stated but needed to reproduce (our reading)

- Which observing blocks and how many per target; target phase centres
- Measured RMS values per target in uJy (only 3-sigma limits in table)
- Dust composition fractions and optical constants for astrosilicate, amorphous carbon, water ice
- Dust grain internal density and scattering treatment details for radmc3d
- Stellar and planetary luminosity inputs and grid resolution for RT
- Number of photons and radial/vertical grid setup
- Image size, cell size, clean threshold, masking
- Primary beam correction and flux calibrator
- Method for extracting RMS (region used)

## Analysis recipe

1. **Image continuum and measure RMS**: tclean natural-weighted image of combined spws; RMS from CLEANed images; 3 sigma used as flux upper limit  
  > "The RMS value for each dataset was calculated from the CLEANed images and are reported in Table" (2 Data description)
   - software: CASA, tclean
   - parameter: natural weights, CASA v.5.2  
  > "(CASA v.5.2, task `tclean`) with ‘natural’ weights" (2 Data description)
   - fitting: _not stated_
   - validation: No sources were detected  
  > "No sources were detected in our observations." (2 Data description)
2. **Radiative transfer disc models to convert flux limit to dust mass limit**: Viscous self-similar surface density disc, vary disc mass until model 1.3 mm flux equals 3 sigma limit, with radmc3d  
  > "we varied the disc mass until the 3$\sigma$ flux upper limit is matched for each disc" (3 CPD models)
   - software: RADMC-3D
   - parameter: slope -1; r_c = 0.4 or 0.04 R_Hill; minimum radius r_c/10; aspect ratio 0.1; 2 deg inclination to planet orbit  
  > "A constant disc vertical aspect ratio of 0.1 is assumed." (3 CPD models)
   - parameter: dust size 1 um to 1 cm, exponent -3.5; opacity 2.3 cm2/g at 1.3 mm  
  > "This yields an absorption opacity of 2.3 cm$^2$ g$^{-1}$ at 1.3 mm." (3 CPD models)
   - assumption: Disc inclination 30 deg from face on (beta Pic b 85 deg)  
  > "we assumed disc inclinations of $30\deg$ from face on for all systems" (3 CPD models)
   - assumption: Star and planet luminosities heat dust; anisotropic scattering included  
  > "The star and planet luminosities are included as energy sources that set the dust temperature." (3 CPD models)
   - fitting: _not stated_
   - validation: Scale-height test for PZ Tel changes flux by <~10%; comparison with Ricci2017b limits  
  > "found that a more realistic scale-height only affects the emitted fluxes by $\ensuremath{\lesssim}$10%" (footnote 5)
3. **Compare to viscous evolution model**: alpha-disc similarity solution until 1 Myr then exponential decay with truncation at 0.4 R_Hill; compare dust mass vs age  
  > "Therefore, for the evolution after 1 Myr instead we used equation 5 in (cite: Rosotti2018)" (4.1 Viscous evolution)
   - parameter: alpha = 1e-4 and 1e-3; disc temperature 40 K; dissipation 1 Myr; initial solid mass 1e-4 Mp  
  > "The dashed and dotted lines represent models with $\alpha=10^{-4}$ and $10^{-3}$, respectively." (4.1 Viscous evolution)
   - assumption: gas-to-dust 100; grain density 1 g/cm3  
  > "gas-to-dust ratio of 100" (4.1 Viscous evolution)
   - fitting: _not stated_
   - validation: _not stated_
4. **Compare to collisional (debris-like) evolution**: Marino2017 collisional model with extreme favourable parameters  
  > "we set the rest of the parameters to extremes to obtain the most favourable condition to detect such disc" (4.2 Collisional evolution)
   - parameter: e=0.01, I=0.005; disc radius 0.4 R_H width 0.5; planet 30 au, 3 MJup; max planetesimal 100 km; initial solid mass 1e-3 Mp  
  > "a large maximum planetesimal size of 100 km" (4.2 Collisional evolution)
   - fitting: _not stated_
   - validation: _not stated_
5. **Lower limit on maximum grain size**: D_max = 2 cm (1e-4 Mp/Mdust)^2 assuming q=-3.5 and total solids 1e-4 Mp, using the larger limit of both disc sizes  
  > "$D_{\max}=2\ \mathrm{cm} \left(\frac{10^{-4} M_\mathrm{p}}{M_\mathrm{dust}}\right)^2," (4.3 Maximum grain sizes)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.2: ALMA pipeline calibration and tclean imaging  
  > "(CASA v.5.2, task `tclean`)" (2 Data description)
- **RADMC-3D** : Radiative transfer to compute 1.3 mm flux of discs  
  > "We input our model into the radmc3d radiative transfer (RT) code to calculate the total flux expected at 1.3 mm" (3 CPD models)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 3 sigma flux limit PZ Tel | 84 | not stated | uJy | 1 | / PZ Tel b       / 21             / 47             / 1.0                    / 1.32                  / 5250           / 25             / 38                        / 0.25                    / 2700                               / 84 |
| 3 sigma flux limit kappa And | 180 | not stated | uJy | 1 | / $\kappa$ And b / 47             / 50             / 2.5                    / 2.3                   / 11500          / 53             / 22                        / 0.25                    / 2040                               / 180 |
| Mmax/Mp PZ Tel b (0.4 / 0.04 R_Hill) | 2.5e-7 / 2.0e-7 | not stated | dimensionless | 2 | 2.5$\times$10$^{-7}$           / 2.0$\times$10$^{-7}$ |
| Mmax/Mp 51 Eri b (0.4 R_Hill) | 2.2e-6 | not stated | dimensionless | 2 | 2.2$\times$10$^{-6}$ |
| Mmax/Mp AB Pic b (0.4 / 0.04 R_Hill) | 5.0e-6 / 2.4e-6 | not stated | dimensionless | 2 | 5.0$\times$10$^{-6}$           / 2.4$\times$10$^{-6}$ |
| Mmax/Mp kappa And b (0.4 / 0.04 R_Hill) | 9.0e-7 / 1.4e-6 | not stated | dimensionless | 2 | 9.0$\times$10$^{-7}$           / 1.4$\times$10$^{-6}$ |
| Dust opacity at 1.3 mm | 2.3 | not stated | cm2 g-1 | 2 | This yields an absorption opacity of 2.3 cm$^2$ g$^{-1}$ at 1.3 mm. |
| Lower limit on D_max for most sources | >1 | not stated | m | 5 | The non detections translate to a value of $D_{\rm max} >$1 metre for most sources. |

## Qualitative findings

- Continuum at 1.3 mm undetected for all four systems  
  > "Continuum emission at 1.3 mm is undetected for any of the systems." (abstract)
- Flux limit for 51 Eri b gives no constraint in the compact disc case because the disc is highly optically thick  
  > "our flux upper limit for 51 Eri b does not place a constraint on the disc mass in the small disc scenario." (3 CPD models)

## Claim tuples

- H: Do young directly-imaged planets host enough mm dust to form regular satellite systems (~1e-4 Mp)? | E: ALMA 1.3 mm observations plus RADMC-3D models for two disc sizes | R: All dust mass upper limits are below ~1e-4 Mp (limits ~1e-7 to 5e-6 Mp) | F: Not enough mm dust; dust has grown to larger bodies or satellites formed | **supported**
- H: Can viscous or collisional evolution explain the non-detections? | E: Compare limits with viscous and collisional evolution models vs age | R: Collisional dust predicted orders of magnitude below limits; viscous high-alpha models lie below the limits | F: Either fast CPD evolution, radial drift or growth to large low-opacity objects | **partially**
- H: Dust grows beyond metre sizes quickly | E: Derive D_max lower limits from the limits | R: D_max > 1 m for most sources | F: Growth to moonetesimals in <~10 Myr | **partially**

## Reasoning

- Why this data: Directly-imaged companions have known temperatures, masses and locations, enabling dust mass limits  
  > "Since these are directly-imaged companions, there is knowledge of their temperatures, masses and locations." (abstract)
- Why this method: _not stated_
- Alternative: Planets may simply not form satellites  
  > "could also imply that these planets do not form satellites" (4.3 Maximum grain sizes)
- How they decided it was enough: _not stated_
- Limitation (authors): System ages uncertain by ~50%  
  > "the age of these systems is uncertain and could vary by $\sim$50%" (4.1 Viscous evolution)
- Limitation (authors): Gas (CO) not analysed  
  > "Searching for low-level gas in these systems is beyond the scope of this paper" (2 Data description)
- Caveat (inferred, ours): Limits depend on assumed opacity, temperature and disc size/geometry
- Caveat (inferred, ours): Brown dwarf companions with masses up to 38 MJup used as planets
- Caveat (inferred, ours): Limits only constrain mm-sized dust, not mass in larger bodies
- Caveat (inferred, ours): Viscous model depends on alpha and assumed temperature

## Reproducibility

- Data public (paper): Project IDs given; public status not explicitly stated  
  > "project IDs `2015.1.01210.S` and ` 2016.1.00358.S`" (2 Data description)
- Products in archive: _not stated_
- Missing: Per-target RMS values and imaging parameters
- Missing: Full RT model inputs (opacity composition, grids)
- Missing: Viscous model details (planet mass grid, Zhu2018 viscosity formula inputs)
- Data volume (inferred): ~tens of GB for four targets
- Score (inferred): 3/5, Data public and recipe outlined, but imaging and RT parameters are incomplete.
- Rediscovery candidate: no, RT setup underspecified; imaging details missing.

## Links

- Method: (cite: Dullemond2012) (RADMC-3D code)
- Method: (cite: Marino2017) (collisional evolution model)
- Method: (cite: Rosotti2018) (viscous decay of truncated disc)
- Companion: (cite: Matra2019) (beta Pic b ALMA limit)
- Companion: (cite: Ricci2017b) (prior limits for comparison)

## Checks

```json
{
 "quotes": 69,
 "quotes_ok": 69,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 88,
  "stated": 53,
  "rate": 0.602
 },
 "evidence_ok": true
}
```
