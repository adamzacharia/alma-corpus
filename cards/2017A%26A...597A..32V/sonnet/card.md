# Cavity and other radial substructures in the disk around HD 97048

`2017A&A...597A..32V` | Astronomy and Astrophysics 2017 | first author: van der Plas, G. | arXiv: 1609.02488 | DOI: 10.1051/0004-6361/201629523

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: Does the Herbig Ae/Be disk around HD 97048 host the predicted ~34 au central cavity, and what is its radial (sub)mm structure?  
  > "We aim to resolve the 34$\pm$ 4 au central cavity predicted by Maaskant et al. (2013) and to investigate the structure of the disk." (abstract)
- Target **HD 97048**: coordinates _not stated_; z/distance 158 (+17/-14) pc  
  > "HD 97048 is a 3 Myr (cite: 2006Sci...314..621L), 2.5 M$_\ensuremath{\odot}$ (cite: 2007A&A...470..625D) HAeBe with spectral type A0 at a distance of 158$^{+17}_{-14}$ parsec (cite: 2007A&A...474..653V)." (Introduction); distance from van Leeuwen 2007 (Hipparcos)  
  > "HD 97048 is a 3 Myr (cite: 2006Sci...314..621L), 2.5 M$_\ensuremath{\odot}$ (cite: 2007A&A...470..625D) HAeBe with spectral type A0 at a distance of 158$^{+17}_{-14}$ parsec (cite: 2007A&A...474..653V)." (Introduction)
- Target **ISO-ChaI 126**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00658.S, 2012.1.00031.S
- bands: ALMA Band 7 (0.853 mm) and Band 3 (2.94 mm); ATCA 5.5-97 GHz  
  > "We image the disk around HD 97048 using ALMA at 0.85 mm and 2.94 mm, and ATCA (multiple frequencies) observations." (abstract)
- frequencies and spectral setup: Band 7: two TDM continuum windows at 345.8 and 356.7 GHz, two FDM windows for J=3-2 and J=4-3 (105 and 103 m/s resolution, 0.23 GHz bandwidth). Band 3: TDM windows at 101.9, 103.9, 113.1 GHz, FDM J=1-0 window at 105.2 GHz (159 m/s)  
  > "These two TDM spectral windows were centred st 345.8 GHz and 356.7 GHz." (2.2 ALMA cycle 2 band 7 data); "The fourth spectral window was configured in FDM to target the J=1-0 line and centered at 105.2 GHz, with a spectral resolution of 159 m s$^{-1}$ and a total bandwidth of 0.117 GHz." (2.3 ALMA Cycle 1 band 3 data)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: Band 7: 21.4-555.5 m; Band 3: 15.8-462.9 m  
  > "The array configuration provided baselines ranging between 15.8 and 462.9 meters." (2.3 ALMA Cycle 1 band 3 data)
- angular resolution: Band 7 beam 0.63x0.36 arcsec (Briggs), 0.60x0.32 (uniform), 0.53x0.31 (superuniform)  
  > "which results in a restoring beam of respectively 0.63$''$ $\times$ 0.36$''$ at PA = 19$^\circ$ (Briggs)" (2.2 ALMA cycle 2 band 7 data)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: Band 7: 430 s; Band 3: 72.6 s  
  > "ALMA Early Science Cycle 2 observations were conducted on 22 May 2015 with 430 seconds of total time on HD 97048" (2.2 ALMA cycle 2 band 7 data)
- observing dates: Band 7: 22 May 2015; Band 3: 1 December 2013  
  > "ALMA Early Science Cycle 1 observations were conducted on 1 December 2013 with 72.6 seconds of total time on HD 97048" (2.3 ALMA Cycle 1 band 3 data)
- pi or archival as stated: Band 7 PI G. van der Plas; Band 3 data from Dunham et al. 2016 program  
  > "on 1 December 2013 with 72.6 seconds of total time on HD 97048 (cite: 2016ApJ...823..160D)" (2.3 ALMA Cycle 1 band 3 data)
- Line: CO J=1-0 (not stated)
- Line: CO J=3-2 (not stated)
- Line: HCO+ J=4-3 (not stated)
- Other facility **ATCA**: Multi-frequency 5.5-97 GHz continuum observations, including 7 mm high-resolution imaging  
  > "High spatial resolution 7–9 mm imaging observations of HD 97048 were conducted on 30 and 31 August 2014 under project C1794." (2.1 ATCA data)
- Other facility **SEST**: 1.3 mm fluxes for SED  
  > "complemented by 1.3 mm SEST fluxes (cite: 1993A&A...276..129H; 1998A&A...336..565H)" (3.1 Continuum emission)
- Other facility **Herschel**: Detections used in ISO-ChaI 126 spectral index  
  > "complemented by Herschel detections reported by (cite: 2012A&A...545A.145W)" (3.3 ISO-ChaI 126)
- External data: MCFOST starting disk model parameters from SED and mid-IR  
  > "We use the MCFOST model parameters from a model based on the SED and mid-IR observations of HD 97048 (cite: 2007A&A...470..625D)" (4.1 Radiative transfer modeling) [from Doucet et al. 2007 (cite: 2007A&A...470..625D)]
- External data: Proper motion correction  
  > "We shift all images using the proper motion correction found in (cite: 2007A&A...474..653V)" (2.2 ALMA cycle 2 band 7 data) [from van Leeuwen 2007 (cite: 2007A&A...474..653V)]
- External data: Dust opacity kappa_1.3mm=2.3 and kappa~nu^0.4  
  > "following (cite: 2013ApJ...771..129A)" (4.7 A disk around ISO-ChaI 126) [from Andrews et al. 2013 (cite: 2013ApJ...771..129A)]
- External data: Dust temperature 15 K for ISO-ChaI 126 disk  
  > "to be 15 K (cite: 2016ApJ...819..102V)" (4.7 A disk around ISO-ChaI 126) [from van der Plas et al. 2016 (cite: 2016ApJ...819..102V)]

## Processing

### Calibration

- pipeline or manual: Band 7: CASA pipeline plus extra flagging; Band 3: provided reduction script  
  > "The data were calibrated using the *Common Astronomy Software Applications* pipeline (cite: 2007ASPC..376..127M), after which some additional flagging was performed." (2.2 ALMA cycle 2 band 7 data)
- casa version: CASA 4.3 (Band 3)  
  > "The data were calibrated using the provided data reduction script and CASA version 4.3." (2.3 ALMA Cycle 1 band 3 data)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Band 3 Ganymede; Band 7 J1107-448  
  > "| ALMA Band 7    | 2015 May 22 | 36           | 7m10s          | 21.6 to 555.5   | 687      | J1107-448  | J1337-1257 | J1058-8003 |" (Table 1 (observations))
- flux scale uncertainty: ~10% ALMA, ~20% ATCA  
  > "We estimate the absolute flux calibration to be accurate within $\sim$10%." (2.2 ALMA cycle 2 band 7 data)
- self calibration: Phase and amplitude self-cal on continuum; solutions applied to lines  
  > "we perform self-calibration on both the phase and amplitude, resulting in a final dynamical range of $\approx$ 1200 and a RMS of 0.20 mJy beam$^{-1}$." (2.2 ALMA cycle 2 band 7 data)

### Imaging

- task: CASA CLEAN; MIRIAD CLEAN for ATCA  
  > "we image the disks with the *CLEAN* task in CASA (cite: 1974AAS...15..417H)" (2.2 ALMA cycle 2 band 7 data)
- deconvolver: _not stated_
- weighting robust: Band 7: Briggs robust=0.5, uniform, superuniform; Band 3 continuum uniform, lines Briggs robust=0.5; ATCA natural  
  > "using Briggs (robust = 0.5), uniform and superuniform weighting" (2.2 ALMA cycle 2 band 7 data)
- uv taper: Long-baseline image uses only baselines >160 kλ with superuniform weighting  
  > "We also reconstructed the images using only baselines above 160 k$\lambda$" (2.2.1 Imaging the long baselines)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: CASA uvcontsub  
  > "subtracted the continuum emission using the CASA task *uvcontsub*" (2.2 ALMA cycle 2 band 7 data)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: Band 3 continuum 2.36x1.40 arcsec PA -39; Band 3 line 2.21x1.43 PA -38; long-baseline Band 7 0.48x0.26 PA 18  
  > "we obtain a restoring beam of 2.36$''$ $\times$ 1.40$''$ at PA = -39$^\circ$." (2.3 ALMA Cycle 1 band 3 data)
- final rms: Band 7 continuum 0.20 mJy/beam; Band 3 continuum 0.18 mJy/beam; line per-channel RMS 19.5-77.5 mJy/beam  
  > "Self-calibration on both the phases and the amplitude results in a continuum RMS of 0.18 mJy beam$^{-1}$." (2.3 ALMA Cycle 1 band 3 data)

### Inherited from earlier work

- Band 3 data originate from a previously published program  
  > "72.6 seconds of total time on HD 97048 (cite: 2016ApJ...823..160D)" (2.3 ALMA Cycle 1 band 3 data) [from Dunham et al. 2016 (cite: 2016ApJ...823..160D)]
- Radiative transfer starting model  
  > "We use the MCFOST model parameters from a model based on the SED and mid-IR observations of HD 97048 (cite: 2007A&A...470..625D)" (4.1 Radiative transfer modeling) [from Doucet et al. 2007]
- Planet mass from simulations  
  > "based on simulation parameters adopted for Fig. 17 in (cite: 2016MNRAS.459.2790R)" (4.6) [from Rosotti et al. 2016]

### Not stated but needed to reproduce (our reading)

- Cell size, image size, and masks for CLEAN
- Self-calibration solution intervals and number of iterations
- Line-free channels for uvcontsub
- uvmem regularization parameters
- MCFOST full parameter set (grain sizes, masses, scale height) and fit criterion
- Fitting method for power laws and spectral indices (weights)
- Rest frequencies of lines
- Source coordinates

## Analysis recipe

1. **Fit continuum size, flux, inclination and PA**: Fit a disk (ALMA) or Gaussian/point (ATCA) to visibilities  
  > "We extract the size and flux of HD 97048 by using the CASA task *uvmodelfit* to fit a disk to the visibility data" (2.2 ALMA cycle 2 band 7 data)
   - software: CASA uvmodelfit, MIRIAD uvfit
   - fitting: _not stated_
   - validation: _not stated_
2. **Image continuum and reconstruct super-resolved images**: CLEAN with several weightings, long-baseline imaging, and MEM (uvmem)  
  > "We use the *uvmem* algorithm (cite: 2006ApJ...639..951C; 2015ApJ...811...92C; 2015ApJ...812..126C)" (2.2.2 MEM image reconstruction)
   - software: CASA, uvmem
   - fitting: _not stated_
   - validation: _not stated_
3. **Radial surface brightness profile and power-law fits**: Deproject superuniform image, collapse radially, fit three power laws a0 r^a1 between 0.3 and 2.6 arcsec  
  > "We fit a power law to these 3 sections of the form *a$_0$ $\times$ r$^{a_1}$* between 0.3 and 2.6$''$, separated at 1.05$''$ and 1.95$''$." (3.1 Continuum emission)
   - fitting: _not stated_
   - validation: _not stated_
4. **Model gap vs ring with radiative transfer**: MCFOST model with Gaussian gap or extra ring, simobserve to visibilities, CLEAN, compare visibilities and images  
  > "we use the CASA tasks *simobserve* to convert the image into visibilities, as would be observed with a similar antenna configuration and on-sky properties as for our ALMA band 7 observations." (4.1 Radiative transfer modeling)
   - software: MCFOST, CASA simobserve, CASA CLEAN
   - fitting: Manual exploration; no confidence intervals  
  > "we do not determine confidence intervals for our derived parameters." (4.1 Radiative transfer modeling)
   - validation: Residuals and deprojected visibilities compared  
  > "We show the ring model, the residuals and the deprojected visibilities in Fig. [10]" (4.1 Radiative transfer modeling)
5. **Spectral index of SED**: Linear least squares fit to 1-10 mm SED; beyond 10 mm subtract extrapolated power law and fit  
  > "A linear least squares fit to the 1–10 mm portion of the SED yields a spectral index $\alpha$ (where $F \propto \nu^\alpha$) of 3.1 $\pm$ 0.1." (3.1 Continuum emission)
   - fitting: _not stated_
   - validation: _not stated_
6. **Line moment maps, systemic velocity and emitting radii**: Moment 0, 1, 8 maps; radius from line wing half width assuming Keplerian rotation, i=41.4 deg, 2.5 Msun  
  > "These values can be translated to an emitting radius of 13.4 and 27.0 au, assuming the gas is in Keplerian rotation in a disk inclined by 41.4$^\circ$ around a 2.5 M$_{\odot}$ star." (3.2 CO and emission)
   - fitting: _not stated_
   - validation: _not stated_
7. **Disk mass of ISO-ChaI 126**: Optically thin isothermal dust mass at 43 GHz  
  > "We estimate the emitting dust mass at 43 GHz, by assuming the disk is isothermal and optically thin" (4.7)
   - assumption: T_dust=15 K, gas-to-dust 100, kappa_1.3mm=2.3 with kappa~nu^0.4  
  > "Using a gas-to-dust ratio of 100, these assumptions result in a total disk mass of 0.0082 M$_\ensuremath{\odot}$" (4.7)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.3 (Band 3): Calibration, CLEAN, uvmodelfit, uvcontsub, simobserve  
  > "We used the standard reduction tools within the CASA package to calibrate and combine the data." (2.2 ALMA cycle 2 band 7 data)
- **MIRIAD** : ATCA calibration, imaging, uvfit, uvaver, uvmodel  
  > "The data were calibrated using the MIRIAD package (cite: 1995ASPC...77..433S)." (2.1 ATCA data)
- **IDL** : Fitting binned ATCA visibilities  
  > "This was subsequently treated in IDL, where the channel-averaged and binned visibilities were fitted" (2.1 ATCA data)
- **uvmem** : MEM image reconstruction  
  > "We use the *uvmem* algorithm" (2.2.2 MEM image reconstruction)
- **MCFOST** : Radiative transfer disk models  
  > "We use the 3D, Monte-Carlo based, radiative transfer code MCFOST" (4. Discussion)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Dust cavity radius (853 um) | 43 | ±3 | au | 4 | There is a dust cavity visible in the 853 $\mu$m continuum emission out to 43 $\pm$3 au. |
| Continuum outer radius | 2.25 (355) | 0.01 | arcsec (au) | 1 | / ALMA band 7 / 0.853 / 2253.16 / 0.96 / D / 2.25 (0.01) / 41.4$^{\pm 0.9}$ / 4.5 (0.1) / |
| Disk inclination and PA | 41.4 and 4.5 | ±0.9, ±0.1 | degrees | 1 | We adopt the disk inclination of 41.4 $\pm$ 0.9$^\circ$ and the position angle of 4.5 $\pm$ 0.1$^\circ$ |
| Band 7 flux at 0.853 mm | 2253.16 | 0.96 | mJy | 1 | / ALMA band 7 / 0.853 / 2253.16 / 0.96 / D / |
| Power-law fits [a0,a1] | [0.5,-0.8], [0.7,-5.7], [14.3,-10.4] | not stated | dimensionless | 3 | \[0.5, -0.8\], \[0.7, -5.7\] and \[14.3, -10.4\], respectively. |
| Spectral index 1-10 mm | 3.1 | 0.1 | dimensionless | 5 | of 3.1 $\pm$ 0.1. |
| Spectral index beyond 10 mm | 0.4 | 0.6 | dimensionless | 5 | $\alpha$ = 0.4 $\pm$ 0.6. |
| Systemic velocity | 4.75 | 0.1 | km/s | 6 | v$_{LSR}$ = 4.75 $\pm$ 0.1 km s$^{-1}$ |
| Gas emitting radii (J=3-2, J=4-3) | 13.4 and 27.0 | not stated | au | 6 | These values can be translated to an emitting radius of 13.4 and 27.0 au |
| Line outer radii J=1-0, 3-2, 4-3 | 4.2, 5.2, 2.9 | not stated | arcsec | 6 | is 4.2$''$, 5.2$''$ and 2.9$''$, respectively. |
| Maximum planet mass opening cavity | 0.12-0.71 | not stated | M_jup | 0 | we estimate a maximum planetary mass between 0.12 and 0.71 M$_{jup}$ |
| ISO-ChaI 126 spectral index | 1.9 | 0.2 | dimensionless | 5 | yield a spectral index $\alpha$ = 1.9 $\pm$ 0.2 |
| ISO-ChaI 126 disk mass | 0.0082 (0.80% of system mass) | not stated | M_sun | 7 | these assumptions result in a total disk mass of 0.0082 M$_\ensuremath{\odot}$, or 0.80% of the total system mass. |

## Qualitative findings

- The 34 GHz ATCA image does not show the cavity, likely because unresolved free-free emission fills it in  
  > "The disk cavity is not detected at 9 mm because free-free emission from the star fills in the cavity at our spatial resolution." (Conclusions)
- J=4-3 velocity map shows non-Keplerian 's'-shaped pattern inside the cavity  
  > "shows an ‘s’ shaped pattern, characteristic for non-keplerian in-falling gas or an inner disk warp" (4.4)

## Claim tuples

- H: HD 97048 has a dust cavity as predicted | E: ALMA Band 7 imaging, MEM, and MCFOST modelling | R: Cavity radius 43±3 au at 853 um | F: A cavity is resolved, with size varying with wavelength/tracer | **supported**
- H: Additional radial structure is a gap or a ring | E: MCFOST gap and ring models compared to Band 7 data | R: Both reproduce data similarly; gap at ~90 au or ring at ~150 au | F: Cannot distinguish gap from ring | **partially**
- H: Gas inside the cavity is non-Keplerian, suggesting a companion | E: J=4-3 velocity map | R: S-shaped pattern in cavity | F: Suggests orbiting body or inner disk warp | **partially**
- H: Grain growth has occurred | E: SED spectral index 1-10 mm | R: alpha = 3.1±0.1 | F: Consistent with mm-sized grains | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Point plus disk and point plus ring models at 33/35 and 38/40 GHz were unsatisfactory  
  > "Models for a ‘point plus disk’ and ‘point plus ring’ were also tried at 33/35 and 38/40 GHz, but the results were unsatisfactory" (4.3)
- How they decided it was enough: _not stated_
- Limitation (authors): Limited resolution cannot distinguish gap from ring  
  > "the limited spatial resolution of our observations does not allow us to differentiate between the presence of a gap or a ring" (4.5)
- Caveat (inferred, ours): Model fits are manual with no uncertainties
- Caveat (inferred, ours): Foreground absorption affects CO line cores
- Caveat (inferred, ours): Resolution inside the cavity is coarse for kinematic claims
- Caveat (inferred, ours): Free-free fill-in inferred from sparse, multi-epoch ATCA data

## Reproducibility

- Data public (paper): ALMA project codes given; archival data  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA# 2013.1.00658.S and 2012.1.00031.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Imaging cell/image sizes and masks
- Missing: Self-cal parameters
- Missing: MCFOST full model and fit procedure
- Missing: Power-law fit details
- Data volume (inferred): ~ a few GB for the ALMA data
- Score (inferred): 5/5, ALMA data are public and key numbers are stated, but imaging, self-cal and model parameters are incomplete and modeling is manual.
- Rediscovery candidate: no, Modelling is manual and incompletely specified, so the main results cannot be redone mechanically.

## Links

- Method: Rosotti et al. 2016 (cite: 2016MNRAS.459.2790R) (Minimum planet mass estimate)
- Method: Pinte et al. 2006 (cite: 2006A&A...459..797P) (MCFOST code)
- Companion: Maaskant et al. 2013 (cite: 2013A&A...555A..64M) (Predicted cavity from SED and Q band)
- Companion: Walsh et al. 2016 (cite: 2016arXiv160902011W) (Companion ALMA analysis of HD 97048)

## Checks

```json
{
 "quotes": 75,
 "quotes_ok": 75,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 13,
 "numeric_problems": 0,
 "fill": {
  "facts": 87,
  "stated": 51,
  "rate": 0.586
 },
 "evidence_ok": true
}
```
