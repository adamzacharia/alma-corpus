# ALMA Measurements of Circumstellar Material in the GQ Lup System

`2017ApJ...835...17M` | The Astrophysical Journal 2017 | first author: MacGregor, Meredith A. | arXiv: 1611.06229 | DOI: 10.3847/1538-4357/835/1/17

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, exoplanets
- Question: What are the properties of the circumprimary disk of GQ Lup A (size, geometry, stellar mass) and is there a circumplanetary disk around the companion GQ Lup b?  
  > "resolve the disk of dust and gas surrounding the primary star, GQ Lup A, and provide deep limits on any circumplanetary disk surrounding the companion, GQ Lup b." (abstract)
- Target **GQ Lup**: coordinates RA 15h49m12.082861, Dec -35d39m05.48071 (J2000, June phase center)  
  > "The GQ Lup system is located in the $3\pm2$ Myr-old (cite: alc14) Lupus I cloud (cite: tac96) at a distance of $156\pm50$ pc (cite: neu08)." (2 The GQ Lup System); "The phase center for the June observations was specified at $\alpha=15^\text{h}49^\text{m}12.082861$, $\delta=-35\ensuremath{^\circ}39\ensuremath{'}05.48071\ensuremath{''}$ (J2000)" (3 Observations); z/distance 156±50 pc (Gaia DR1 Lupus I: 156.3±7.3 pc)  
  > "The GQ Lup system is located in the $3\pm2$ Myr-old (cite: alc14) Lupus I cloud (cite: tac96) at a distance of $156\pm50$ pc (cite: neu08)." (2 The GQ Lup System); "The phase center for the June observations was specified at $\alpha=15^\text{h}49^\text{m}12.082861$, $\delta=-35\ensuremath{^\circ}39\ensuremath{'}05.48071\ensuremath{''}$ (J2000)" (3 Observations); distance from Neuhauser et al. 2008; Gaia DR1 Lindegren et al. 2016  
  > "The GQ Lup system is located in the $3\pm2$ Myr-old (cite: alc14) Lupus I cloud (cite: tac96) at a distance of $156\pm50$ pc (cite: neu08)." (2 The GQ Lup System); "The phase center for the June observations was specified at $\alpha=15^\text{h}49^\text{m}12.082861$, $\delta=-35\ensuremath{^\circ}39\ensuremath{'}05.48071\ensuremath{''}$ (J2000)" (3 Observations)

## Data provenance

- ALMA projects: 2013.1.00374.S
- bands: Band 7 (870 um)  
  > "The GQ Lup system was observed with ALMA in Band 7 (870 $\mu$m)" (3 Observations)
- frequencies and spectral setup: Four basebands centered 331, 333, 343, 345 GHz; 331 and 345 GHz have 3840 channels over 1.875 GHz; other two 128 channels over 2 GHz  
  > "The basebands with the targeted spectral lines, centered at 331 and 345 GHz, each have 3840 channels over a bandwidth of 1.875 GHz, while the other two basebands each have only 128 channels over a bandwidth of 2 GHz." (3 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15 to 1574 m  
  > "2015 Aug 28  |    40    |   $15-1574$" (Table 1)
- angular resolution: ~0.3 arcsec (~45 AU)  
  > "beam size $\sim0.3\ensuremath{''}$ ($\sim45$ AU)" (abstract)
- max recoverable scale: _not stated_
- sensitivity: continuum rms 50 uJy/beam  
  > "the rms noise level is 50 $\mu$Jy/beam" (4.1 Continuum Emission)
- time on source: ~30 min per SB (31.3, 31.1, 35.0 min)  
  > "2015 June 14 |    41    |   $16-784$    |  0.6   |     31.3" (Table 1)
- observing dates: 2015 June 14, June 15, August 28  
  > "on 2015 June 14 with 41 operational antennas and on 2015 June 15 with 37 operational antennas" (3 Observations)
- pi or archival as stated: _not stated_
- Line: 12CO J=3-2 (345.79599 GHz)
- Line: 13CO J=3-2 (330.58797 GHz)
- External data: Dust temperature-luminosity relation T_dust=25(L/Lsun)^{1/4}  
  > "we use the dust temperature-stellar luminosity relationship of (cite: and13): $T_\text{dust}=25(L/L_\odot)^{1/4}$." (4.1 Continuum Emission) [from (cite: and13)]
- External data: Dust opacity kappa_nu = 10(nu/1e12 Hz) cm2/g  
  > "we adopt the frequency-dependent dust opacity $\kappa_\nu = 10(\nu/10^{12}\text{ Hz})$ cm$^{2}$ g$^{-1}$ from (cite: beck90)" (4.1 Continuum Emission) [from (cite: beck90)]

## Processing

### Calibration

- pipeline or manual: ALMA-delivered calibration scripts run for each SB  
  > "The raw datasets were delivered with calibration scripts provided by ALMA staff." (3 Observations)
- casa version: CASA 4.5.0  
  > "using the `CASA` package (version 4.5.0) to generate calibrated visibilities" (3 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan and Ceres  
  > "The absolute flux calibration was derived from observations of Titan and Ceres" (3 Observations)
- flux scale uncertainty: <10%  
  > "with a systematic uncertainty estimated at less than $10\%$" (3 Observations)
- self calibration: single iteration of phase-only self-calibration, then averaged to 30 s  
  > "A single iteration of phase-only self-calibration was employed, after which the visibilities were averaged into 30 second intervals." (3 Observations)

### Imaging

- task: multi-frequency synthesis CLEAN in CASA  
  > "We generated both continuum and CO line images using the multi-frequency synthesis `CLEAN` algorithm in `CASA`." (3 Observations)
- deconvolver: _not stated_
- weighting robust: robust = 0.5  
  > "With robust $=0.5$ weighting, the synthesized beam size is $0.37\ensuremath{''}\times0.23\ensuremath{''}$" (4.1 Continuum Emission)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum subtracted from spectral windows with lines  
  > "For spectral line imaging, the continuum level was subtracted from the spectral windows containing emission lines." (3 Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.37" x 0.23" (58x36 AU), PA -87 deg  
  > "the synthesized beam size is $0.37\ensuremath{''}\times0.23\ensuremath{''}$ ($58\times36$ AU at 156 pc) with a position angle of $-87\ensuremath{^\circ}$" (4.1 Continuum Emission)
- final rms: continuum 50 uJy/beam; 12CO 11 mJy/beam per channel; 13CO 6.5 mJy/beam  
  > "For the $^{13}$CO image, the typical rms noise is 6.5 mJy/beam." (4.2 CO Emission)

### Inherited from earlier work

- Disk forward-modeling framework (DiskJockey) details  
  > "Further details of the modeling framework can be found in (cite: cze15)." (4.2 CO Emission) [from (cite: cze15)]
- Opacity choice for consistency with earlier papers  
  > "For consistency with (cite: bow15) and (cite: ans16), we adopt the frequency-dependent dust opacity" (4.1 Continuum Emission) [from (cite: bow15); (cite: ans16)]

### Not stated but needed to reproduce (our reading)

- Line-free channels and clean thresholds/masks for continuum and CO imaging
- Channel width and velocity resolution of CO cubes
- Image size and cell size
- MCMC sampler, priors, and model grid/inner and outer radii settings for DiskJockey
- Which spectral windows/channels were used in visibility fits
- Self-calibration solution interval

## Analysis recipe

1. **Image continuum and measure flux/size, companion limit**: CLEAN imaging; 2D Gaussian fit to the image; 3 sigma upper limit at GQ Lup b position assuming point source  
  > "By fitting a simple two dimensional Gaussian to the continuum image, we obtain a total flux density for the circumprimary disk of $77.8\pm0.2$ mJy" (4.1 Continuum Emission)
   - software: CASA
   - parameter: robust = 0.5  
  > "With robust $=0.5$ weighting, the synthesized beam size is $0.37\ensuremath{''}\times0.23\ensuremath{''}$" (4.1 Continuum Emission)
   - fitting: _not stated_
   - validation: Compared to SMA and SEST fluxes via spectral index 2.4  
  > "we obtain a flux density at 1.3 mm of $29.7\pm5.4$ mJy, in good agreement with both previous flux density measurements" (4.1 Continuum Emission)
2. **Derive dust masses and CPD limits**: Optically thin mass M=F D^2/(kappa B(T)); optically thick size limit  
  > "For optically thin emission, we can make a simple estimate of the total dust mass ($M_\text{dust}$)" (4.1 Continuum Emission)
   - assumption: kappa=3.4 cm2/g at 870 um; T_dust=24 K (disk A), 18 K (at GQ Lup b); gas-to-dust 100 for total CPD mass  
  > "At 870 $\mu$m, the dust opacity is $\kappa_\nu=3.4$ cm$^{2}$ g$^{-1}$." (4.1 Continuum Emission)
   - fitting: _not stated_
   - validation: Tested alternative T_dust=10 K from van der Plas et al.  
  > "If we take $T_\text{dust}=10$ K, instead, then $M_\text{dust}<0.14$ $M_\oplus$ and $M_\text{tot}<14$ $M_\oplus$." (4.1 Continuum Emission)
3. **Forward-model CO velocity field**: Parametric disk model (self-similar surface density, power-law temperature, Keplerian) with RADMC-3D images, Fourier transformed and sampled at data uv points, chi2 likelihood  
  > "the model visibilities are then evaluated using a $\chi^2$ likelihood function which incorporates the statistical weights on each visibility measurement." (4.2 CO Emission)
   - software: DiskJockey, RADMC-3D
   - parameter: Free parameters: M*, i, PA, r_c, T10, q, Mgas, xi, vsys, RA/Dec offsets  
  > "| $r_c$ | Characteristic radius (AU) | $97.6\pm3.7$ | $46.5\pm1.8$ |" (Table 2)
   - assumption: Constant CO abundance ~1e-4 (ISM-like); vertically isothermal, hydrostatic equilibrium; Keplerian rotation  
  > "A significant caveat to our derived gas mass is that it depends inversely on the CO/H$_2$ abundance ratio, which we assume to be ISM-like $\sim10^{-4}$." (4.2 CO Emission)
   - fitting: Posterior evaluated with chi2 likelihood; sampler and priors not stated  
  > "the model visibilities are then evaluated using a $\chi^2$ likelihood function which incorporates the statistical weights on each visibility measurement." (Results and Analysis, $^{12}$CO and $^{13}$CO Emission)
   - validation: Compared 12CO and 13CO fits; focus on 13CO due to cloud contamination; method validated on spectroscopic binaries; compared to Williams & Best grids  
  > "As a result, we focus on the best-fit parameters from the $^{13}$CO modeling." (4.2 CO Emission)
4. **Gas-to-dust ratio**: Combine 13CO gas mass with dust mass  
  > "we can calculate the gas-to-dust ratio for the circumstellar disk around GQ Lup A to be $4.7\pm0.5$" (4.2 CO Emission)
   - fitting: _not stated_
   - validation: Compared to Lupus disks of Ansdell et al.  
  > "but is comparable to measurements made by (cite: ans16) for circumstellar disks around other T Tauri stars in Lupus" (4.2 CO Emission)

## Software

- **CASA** 4.5.0: Calibration scripts, CLEAN imaging  
  > "using the `CASA` package (version 4.5.0) to generate calibrated visibilities" (3 Observations)
- **DiskJockey** : Forward-modeling CO visibilities  
  > "we forward-model the ${}^{12}$CO and ${}^{13}$CO molecular line emission using the `DiskJockey` package" (4.2 CO Emission)
- **RADMC-3D** : Generating sky images of disk models  
  > "sky-images of a given disk structure are generated using the `RADMC-3D` radiative transfer program" (4.2 CO Emission)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum flux density of GQ Lup A disk | 77.8 | 0.2 | mJy | 1 | we obtain a total flux density for the circumprimary disk of $77.8\pm0.2$ mJy |
| Dust disk FWHM | 59 | 12 | AU | 1 | The circumprimary dust disk is compact with a FWHM of $59\pm12$ AU |
| 3 sigma flux limit on CPD | <0.15 | not stated | mJy | 1 | we determine a $3\sigma$ upper limit on the flux density of any circumplanetary disk surrounding the secondary of $<0.15$ mJy |
| Circumprimary dust mass | 15.10 | 0.04 | Earth masses | 2 | The resulting dust mass is $15.10\pm0.04$ $M_\oplus$. |
| CPD dust mass limit | <0.04 | not stated | Earth masses | 2 | the resulting $3\sigma$ upper limit on the dust mass is $M_\text{dust}<0.04$ $M_\oplus$ |
| CPD optically thick radius limit | <1.1 | not stated | AU | 2 | $R_\text{dust}$ must be $<1.1$ AU |
| Stellar mass GQ Lup A (13CO fit) | 1.03 | 0.15 (0.05 at known distance) | Msun | 3 | The models imply a stellar mass, $M_*$, for GQ Lup A of $1.03\pm0.15$ $M_\odot$. |
| Disk inclination | 60.5 | 0.5 | deg | 3 | the best-fit inclination is $i = 60.5\ensuremath{^\circ}\pm0.5\ensuremath{^\circ}$ and position angle is $PA=346\ensuremath{^\circ} \pm1\ensuremath{^\circ}$ |
| Disk position angle | 346 | 1 | deg | 3 | / $PA$ / Disk position angle ($\ensuremath{^\circ}$) / $346\pm1$ / $346\pm1$ / |
| 13CO characteristic radius | 46.5 | 1.8 | AU | 3 | are $46.5\pm1.8$ AU and log$M_\text{gas}/M_\odot = -3.67\pm0.05$, respectively |
| Gas-to-dust ratio | 4.7 | 0.5 | dimensionless | 4 | gas-to-dust ratio for the circumstellar disk around GQ Lup A to be $4.7\pm0.5$ |
| Systemic velocity (LSRK) | 3.00 | 0.01 | km/s | 3 | The systemic velocity in the LSRK frame is $3.00\pm0.01$ km s$^{-1}$ |

## Qualitative findings

- No evidence of truncation of the CO gas disk by GQ Lup b; gas disk more extended than dust  
  > "The CO emission morphology does not show any indication of truncation of the circumprimary gas disk due to the companion, GQ Lup b." (4.2 CO Emission)

## Claim tuples

- H: GQ Lup b hosts a detectable circumplanetary disk | E: 870 um continuum imaging at GQ Lup b position | R: No detection; 3 sigma <0.15 mJy, M_dust<0.04 Mearth | F: Deep limit disfavors in situ formation via fragmentation/GI with massive long-lived CPDs | **supported**
- H: Constrain stellar mass and disk geometry of GQ Lup A | E: Forward-model 13CO/12CO Keplerian velocity field | R: M*=1.03±0.15 Msun, i=60.5±0.5 deg, PA=346±1 deg | F: Disk inclination much higher than stellar rotation axis estimates; does not exclude in situ formation of companion | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Used 13CO rather than 12CO fit because 12CO may be biased by cloud contamination  
  > "the $^{12}$CO fits may be biased by the cloud contamination evident in the residuals" (4.2 CO Emission)
- How they decided it was enough: _not stated_
- Limitation (authors): Gas mass depends inversely on assumed CO/H2 abundance  
  > "it depends inversely on the CO/H$_2$ abundance ratio, which we assume to be ISM-like $\sim10^{-4}$" (4.2 CO Emission)
- Limitation (authors): Higher angular resolution needed to constrain dust edges and substructure  
  > "Longer baseline observations with higher angular resolution are needed to better constrain the location and sharpness of the dust disk edges" (4.1 Continuum Emission)
- Caveat (inferred, ours): Dust and gas masses depend strongly on assumed temperature and opacity
- Caveat (inferred, ours): Simple parametric disk model; gas-to-dust ratio of 4.7 mixes models with differing assumptions
- Caveat (inferred, ours): 12CO and 13CO radii differ by factor two, indicating model degeneracy
- Caveat (inferred, ours): Distance uncertainty dominates mass error

## Reproducibility

- Data public (paper): ALMA project 2013.1.00374.S cited; code DiskJockey open source  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA #2013.1.00374.S." (Acknowledgments)
- Products in archive: _not stated_
- Code: DiskJockey open source under MIT license  
  > "Open source and freely available at <https://github.com/iancze/DiskJockey> under an MIT license." (footnote 1)
- Missing: Sampler/priors and model setup details for DiskJockey
- Missing: Clean parameters, masks, channel widths
- Data volume (inferred): ~20-50 GB for three SBs (raw), moderate
- Score (inferred): 3/5, Public data, scripts and open-source modeling code, but imaging and fit settings are partly missing.
- Rediscovery candidate: yes, Public data, numerical results (flux, mass, inclination) and a mostly complete recipe with open code.

## Links

- Method: Czekala et al. 2015 (cite: cze15) (DiskJockey forward modeling framework)
- Companion: Schwarz et al. 2016 (cite: sch16) (Orbit and spin of GQ Lup b)
- Related: Lupus ALMA survey (Ansdell et al. 2016)

## Checks

```json
{
 "quotes": 68,
 "quotes_ok": 68,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 71,
  "stated": 47,
  "rate": 0.662
 },
 "evidence_ok": true
}
```
