# Massive dust clumps in the envelope of the red supergiant VY Canis Majoris

`2019A&A...627A.114K` | Astronomy and Astrophysics 2019 | first author: Kamiński, T. | arXiv: 1903.09558 | DOI: 10.1051/0004-6361/201935408

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars
- Question: What is the structure and dust mass of the dusty clumps in the inner envelope of VY CMa, and was their mass underestimated in earlier studies?  
  > "We critically examine the mass constraints on the dusty medium finding that its mass might have been considerably underestimated in earlier studies" (Introduction)
- Target **VY CMa**: coordinates _not stated_; z/distance 1.2 kpc (1.17 kpc also used for proper-motion conversion)  
  > "We adopted a distance of 1.2 kpc (cite: zhang)." (3D radiative transfer model of the dusty envelope); distance from Zhang et al. 2012 (cite: zhang)  
  > "We adopted a distance of 1.2 kpc (cite: zhang)." (3D radiative transfer model of the dusty envelope)

## Data provenance

- ALMA projects: 2013.1.00156.S
- bands: Band 6 and Band 7  
  > "We report ALMA observations obtained in Bands 6 and 7" (2 Observations)
- frequencies and spectral setup: B6: 220.6–224.3, 235.2–237.1, 238.1–240.0 GHz, ~1.3 km/s channels; B7: 343.6–345.4, 345.5–347.2, 355.5–357.3, 357.3–359.2 GHz, 1.7 km/s channels  
  > "The observations covered the spectral ranges 220.6–224.3, 235.2–237.1, 238.1–240.0 GHz at a channel binning of about 1.3 km s$^{-1}$." (2 Observations); "The spectral setup covered four ranges: 343.6–345.4, 345.5–347.2, 355.5–357.3, 357.3–359.2 GHz at a channel width of 1.7 km s$^{-1}$." (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: B6: 33–2193 m; B7: 42–2257 m  
  > "We used the main array with 34 functioning antennas at projected baselines of 33–2193 m." (2 Observations); "Projected baselines of 42–2257 m combined gave a synthesized beam of 115$\times$98 mas at a PA of 61$^\circ$" (2 Observations)
- angular resolution: B6: 173x133 mas PA 70 deg; B7: 115x98 mas PA 61 deg  
  > "The configuration resulted in a beam FWHM of 173$\times$133 mas and with the major axis at a position angle (PA) of 70$^\circ$." (2 Observations)
- max recoverable scale: B6: 0.7 arcsec; B7: ~0.9 arcsec  
  > "The maximum recoverable angular scale (MAS) of 0.7$''$ is much smaller than the entire field of view of 27.5$''$." (2 Observations)
- sensitivity: 27 uJy (B6), 206 uJy (B7), all in-band combined  
  > "The final sensitivities of all in-band observations combined were of 27 $\mu$Jy and 206 $\mu$Jy at Bands 6 and 7, respectively" (2 Observations)
- time on source: B6: 40 min; B7: 71 min  
  > "Band 6 observations took place on 27 Sept. 2015 with 40 min spent on source." (2 Observations); "The combined data are equivalent to 71 min integration on source." (2 Observations)
- observing dates: B6: 27 Sept 2015; B7: 28 June and 27 Sept 2015  
  > "Band 7 observations were acquired in two blocks executed on 28 June and 27 September 2015" (2 Observations)
- pi or archival as stated: PI: T. Kamiński (own program)  
  > "within a project 2013.1.00156.S (PI: T. Kamiński)" (2 Observations)
- Line: CO 3–2 (not stated)
- Other facility **SMA**: 2010 survey and 2017 SWARM observations (279–355 GHz) combined with ALMA B7 for short spacings  
  > "combining the calibrated Band 7 ALMA visibilities with 2010 survey observations of VY CMa obtained with the Submillimeter Array (SMA) in the range 279–355 GHz" (2 Observations)
- Other facility **HST**: archival 2009 F1042M image used for filtering simulation and comparison  
  > "An archival image obtained in 2009 with the HST in the $F1042M$ band ($\sim$1 $\mu$m) was converted into visibilities" (2 Observations)
- Other facility **AAVSO**: visual light curve since 1957  
  > "Regular observations since 1957 have come from AAVSO" (6 Clumps relation to stellar light variations)
- External data: Historical blue light curve 1893–1971 (digitized from scan)  
  > "We converted[^5] his *blue* light curve to an electronic table from a scan of the original study." (6 Clumps relation to stellar light variations) [from Robinson 1970 (cite: Robinson1970)]
- External data: SMA survey observations of VY CMa 2010  
  > "2010 survey observations of VY CMa obtained with the Submillimeter Array (SMA) in the range 279–355 GHz (cite: kamiSurv)" (2 Observations) [from (cite: kamiSurv)]
- External data: Astro-silicate optical constants from DUSTY  
  > "We used opacity and scattering properties of the so-called astro-silicates (cite: DL84) generated in RADMC-3D from the optical constants distributed with DUSTY" (4 3D radiative transfer model) [from (cite: DL84)]
- Simulation/model as data: PHOENIX synthetic stellar spectrum (Teff=3500 K, logg=-0.5)  
  > "The stellar radiation was represented by a synthetic spectrum with $T_{\rm eff}$=3500 K, solar metallicity, and $\log g$=–0.5" (4 3D radiative transfer model)

## Processing

### Calibration

- pipeline or manual: Default CASA pipeline, then phase and amplitude self-calibration  
  > "All the 2015 observations were initially calibrated with the default CASA pipeline in version 4.3.1." (2 Observations); "Both Band 6 and 7 data were also self-calibrated in phase and amplitude." (2 Observations)
- casa version: 4.3.1 (calibration); 4.7 to 5.4 (processing)  
  > "All data were processed in CASA (versions 4.7 to 5.4)" (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: phase and amplitude, with extra flagging  
  > "Extra flagging of bad data was introduced in that procedure." (2 Observations)

### Imaging

- task: clean / tclean  
  > "using the `clean` or `tclean` implementations of the CLEAN algorithm" (2 Observations)
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0.5 unless otherwise stated  
  > "We used the Briggs weighting of visibilities at the robust parameter of 0.5, unless otherwise stated." (2 Observations)
- uv taper: UV taper equivalent to a 450 mas Gaussian beam  
  > "This was somewhat equivalent to smoothing the maps to a Gaussian beam of 450 mas FWHM." (3.1 Main continuum emission features)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Linear fit to visibilities per spectral window over iteratively defined pure-continuum ranges, subtracted as representation of continuum  
  > "we defined relatively reliable ranges with pure continuum which were then used for a simple linear fit to the visibilities of each spectral window" (2 Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: ALMA B7 combined with SMA data, weights recalculated in CASA  
  > "The relative visibility weights of the three datasets were recalculated within CASA" (2 Observations)
- smoothing: Spectral-index maps restored with circular 152 mas beam  
  > "produced from maps restored with a circular beam of 152 mas" (3.2 Spectral index)
- final beam: B6 173x133 mas; B7 115x98 mas  
  > "Projected baselines of 42–2257 m combined gave a synthesized beam of 115$\times$98 mas at a PA of 61$^\circ$" (2 Observations)
- final rms: _not stated_

### Inherited from earlier work

- Clump names VY and C  
  > "we kept the names of features VY and C introduced by (cite: anita)" (3.1 Main continuum emission features) [from (cite: anita)]
- Adopted distance 1.2 kpc  
  > "We adopted a distance of 1.2 kpc (cite: zhang)." (4 3D radiative transfer model) [from (cite: zhang)]
- Stellar parameters consistent with literature  
  > "These stellar parameters are consistent with estimates of (cite: wittkowski)." (4 3D radiative transfer model) [from (cite: wittkowski)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges used for continuum fit
- Self-calibration solution intervals and reference models
- Image size and cell size, deconvolution masks, clean thresholds
- Procedure and values of positional shifts applied to each dataset
- SMA calibration details and relative weights used
- Full RADMC-3D model parameter files and the chosen model among ~1000
- Gaussian fit software and procedure for flux errors
- Pipeline run details for the ALMA data

## Analysis recipe

1. **Image continuum and correct offsets**: Calibrate, self-calibrate, shift positions to match continuum peaks, image with Briggs weighting after visibility-based continuum extraction  
  > "The offset was determined by measuring positions of brightest continuum features and corrected either in the calibrated visibilities or directly by modifying absolute coordinates in processed images" (2 Observations)
   - software: CASA
   - parameter: robust = 0.5  
  > "We used the Briggs weighting of visibilities at the robust parameter of 0.5, unless otherwise stated." (2 Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Assess spatial filtering**: Simulate HST image through ALMA baselines with simobserve/simanalyze  
  > "We used the CASA simulator tasks *simobserve* and *simanalyze* for that purpose." (2 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Measure clump properties**: Sequential 2D Gaussian fits (A, C, VY, B, D) to combined B6 and B7 data, removing each model before the next  
  > "The fit was performed sequentially in the order A, C, VY, B, and D; after fitting a single Gaussian the model profile was removed before fitting the next feature." (3.1 Main continuum emission features)
   - fitting: _not stated_
   - validation: _not stated_
4. **Spectral index map**: Compare B6 and B7 maps restored with common 152 mas beam after aligning peaks  
  > "Maps were also shifted to match their positions of the brightest emission peaks." (3.2 Spectral index)
   - fitting: _not stated_
   - validation: _not stated_
5. **Absorption spectrum of clump C**: LTE simulation of absorption lines with single Tex  
  > "We simulated the absorption components assuming LTE conditions and using CASSIS" (3.4 Resolved observations of clump C)
   - software: CASSIS
   - assumption: Single excitation temperature for all species, LTE  
  > "Single excitation temperature was assumed for all species" (3.4 Resolved observations of clump C)
   - fitting: Best agreement found at Tex = 52 K (3 sigma 37–67 K)  
  > "best agreement with observations was found at $T_{\rm ex}$=52 K (3$\sigma$ range of 37–67 K)" (3.4 Resolved observations of clump C)
   - validation: _not stated_
6. **3D radiative transfer dust model**: RADMC-3D Monte Carlo with Gaussian clumps; images processed in CASA and compared to ALMA; manual trial-and-error over ~1000 models  
  > "best configurations were searched through iterative trial-and-error modifications of the models" (4 3D radiative transfer model)
   - software: RADMC-3D, radmc3dPy, CASA
   - parameter: Cube 2000 AU, 150 grid points per side; 1e5 to 1e9 photons; Modified Random Walk  
  > "we modeled a Cartesian cube of a size of 2000 AU with 150 grid points in each direction." (4 3D radiative transfer model)
   - assumption: Astrosilicates, grain sizes 0.01–1.0 um, n(a) ~ a^-3.5, density 3.5 g/cm3; opacity 0.40 and 0.17 cm2/g at B7 and B6; no iron; Henyey-Greenstein scattering; L=2.7e5 Lsun, Teff 3500 K; d=1.2 kpc  
  > "These assumptions yield dust opacity of 0.40 and 0.17 cm$^2$ g$^{-1}$ at ALMA Bands 7 and 6, respectively." (4 3D radiative transfer model)
   - fitting: No formal fit; aimed to reproduce peak and integrated fluxes within order of magnitude  
  > "We attempted to reproduce the peak and integrated ALMA fluxes of each feature within the order of magnitude." (4 3D radiative transfer model)
   - validation: Treated only as a qualitative toy model  
  > "we treat the radiative transfer modeling performed here only as a qualitative toy model aimed to explore the possible geometries of the system" (4 3D radiative transfer model)

## Software

- **CASA** 4.3.1 (pipeline); 4.7–5.4 (processing): calibration, imaging, simulation of observations  
  > "All data were processed in CASA (versions 4.7 to 5.4)" (2 Observations)
- **RADMC-3D** 0.41: 3D dust radiative transfer  
  > "in the RADMC-3D code (cite: radmc3d) version 0.41" (4 3D radiative transfer model)
- **radmc3dPy** : python analysis routines  
  > "with python analysis routines radmc3dPy" (4 3D radiative transfer model)
- **CASSIS** : LTE simulation of absorption spectra  
  > "We simulated the absorption components assuming LTE conditions and using CASSIS" (3.4 Resolved observations of clump C)
- **PHOENIX** : stellar model spectrum  
  > "generated with the PHOENIX model atmospheres (cite: phoenix) up to 5.5 $\mu$m" (4 3D radiative transfer model)
- **DUSTY** : source of astrosilicate optical constants  
  > "from the optical constants distributed with DUSTY" (4 3D radiative transfer model)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Clump C flux in B6 | 160.39 | 0.10 | mJy | 3 | / C        / 266.4  / –181.9 /   322.6   / $\gtrsim$31  / 181$\pm$15 /   97$\pm$14 / 111$\pm$06  / 160.39$\pm$0.10     /   91.22$\pm$0.69 / |
| Clump A flux in B7 | 467.18 | 0.53 | mJy | 3 | / A        / 184.8  / 529.5  /   560.8   / $\gtrsim$53  / 218$\pm$18 / 141$\pm$15  /   41$\pm$08 /   18.58$\pm$0.12    / 467.18$\pm$0.53  / |
| Spectral index of VY | 1.6 | 0.1 | dimensionless | 4 | Clump VY is most conspicuous through a very low $\alpha$ of 1.6$\pm$0.1. |
| Typical spectral index of clumps A–D | 2.8 | not stated | dimensionless | 4 | The typical spectral index of the overall extended emission of clumps A to D, excluding VY, is 2.8. |
| Brightness temperature of clump C peak in B7 | 163 | not stated | K | 3 | the peak flux in Band 7 translates to a brightness temperature of 163 K |
| Excitation temperature of absorbing gas toward C | 52 | 3 sigma range 37–67 K | K | 5 | best agreement with observations was found at $T_{\rm ex}$=52 K (3$\sigma$ range of 37–67 K) |
| Total dust mass in preferred model | 0.47 | not stated | Msun | 6 | with a total dust mass of 0.47 M$_{\odot}$, 98% of which resides in problematic clump C |
| Dust mass of SW Clump | 1e-3 (lower limit) | not stated | Msun | 6 | The observed fluxes in Band 6 can be roughly reproduced with 1$\cdot\!10^{-3}$ M$_{\odot}$ of dust |
| Flux increase from porosity in clump C | 2.2 | not stated | dimensionless | 6 | increasing the total submm fluxes of clump C by a factor of 2.2 at the same mass of dust involved |

## Qualitative findings

- Continuum divided into five clumps A, B, VY, C, D; SW Clump detected with UV taper  
  > "We divide the source into five main features which appear as individual discrete emission regions, or clumps." (3.1 Main continuum emission features)
- Molecular emission avoids strong continuum regions; dust and gas association inconclusive  
  > "The association of the dust clumps with gas remains therefore inconclusive." (3.3 Relation to gas tracers)

## Claim tuples

- H: Dust mass in VY CMa clumps was underestimated in earlier studies | E: 3D RADMC-3D modeling of Gaussian dust clumps compared to ALMA fluxes | R: Total dust mass 0.47 Msun, mostly in clump C, still underpredicting C flux by ~2 | F: Clump masses may be much higher than earlier estimates, though model is uncertain and may overestimate due to unresolved substructure | **partially**
- H: Clump C is optically thick and cool | E: Brightness temperature and absorption spectrum | R: Tb 163 K; absorbing gas Tex 52 K | F: Dust in C is cooler than nearby molecular gas; possibly thermal decoupling | **partially**
- H: Clump creation is related to stellar light variations | E: Compare clump kinematic ages with historical light curves | R: Ages roughly coincide with periods of enhanced variability | F: Consistent with enhanced variability during or after clump creation, but no unique association | **partially**

## Reasoning

- Why this data: Higher sensitivity than earlier ALMA studies  
  > "based on ALMA observations at sensitivity a few times better than in similar earlier studies" (Introduction)
- Why this method: _not stated_
- Alternative: Internal heating source in clump C dismissed for lack of evidence  
  > "We however dismiss such a possibility as there is no other evidence supporting the presence of an embedded companion." (4.3 Clump C)
- Alternative: Pure iron dust excluded from the model  
  > "we did not include pure iron dust in the model" (4 3D radiative transfer model)
- How they decided it was enough: _not stated_
- Limitation (authors): Model is not unique, has >40 free parameters, ignores substructure; masses may be overestimated  
  > "our masses can be largely overestimated, mainly because the model ignores unresolved substructure within the dusty clumps and dust opacity is essentially unknown" (7 Discussion and conclusions)
- Limitation (authors): Continuum noise underestimated by line-contaminated continuum approach  
  > "In this approach, we took advantage of the continuum flux underlying the numerous spectral lines but underestimate the real noise in the data." (2 Observations)
- Caveat (inferred, ours): No formal fit or uncertainty on model masses; one model chosen from ~1000 by eye
- Caveat (inferred, ours): Dust opacity and gas-to-dust ratio highly uncertain
- Caveat (inferred, ours): Positional shifts between bands could bias the spectral index map
- Caveat (inferred, ours): Model reproduces fluxes only within an order of magnitude

## Reproducibility

- Data public (paper): ALMA data from project 2013.1.00156.S acknowledged; archival  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00156.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Radiative transfer model input files
- Missing: Exact imaging parameters and continuum channel selections
- Missing: SMA data calibration details
- Data volume (inferred): ~100–300 GB for Band 6 and 7 raw data
- Score (inferred): 3/5, ALMA data are public and imaging recipe partly given, but the model is trial-and-error with no released parameters and many imaging details missing.
- Rediscovery candidate: no, Main mass result comes from a non-unique manual RT model that cannot be redone from the stated recipe; only Gaussian fluxes and spectral indices are reproducible.

## Links

- Method: Dullemond et al. 2012 (cite: radmc3d) (RADMC-3D code)
- Method: Robitaille 2010 (cite: RandomWalk) (Modified Random Walk method)
- Companion: O'Gorman et al. 2015 (cite: OGorman) (earlier ALMA SV continuum study)
- Companion: Richards et al. 2014 (cite: anita) (earlier ALMA SV continuum study defining clumps VY and C)
- Companion: Vlemmings et al. 2017 (cite: Vlemmings) (ALMA Band 5 study of clump C)
- Related: ALMA Science Verification observations of VY CMa

## Checks

```json
{
 "quotes": 78,
 "quotes_ok": 78,
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
  "facts": 87,
  "stated": 59,
  "rate": 0.678
 },
 "evidence_ok": true
}
```
