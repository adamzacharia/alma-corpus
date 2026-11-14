# Modeling the Accretion Disk around the High-mass Protostar GGD 27-MM1

`2020ApJ...888...41A` | The Astrophysical Journal 2020 | first author: Añez-López, N. | arXiv: 1911.12398 | DOI: 10.3847/1538-4357/ab5dbc

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, protoplanetary_disks
- Question: Can irradiated alpha-accretion disk models used for low-mass stars fit the 1.14 mm ALMA dust image of the GGD 27-MM1 high-mass protostar disk, and what physical parameters result?  
  > "The main goal is to investigate if the assumptions that are usually adopted for disks around low-mass stars can be roughly extrapolated to the case of massive stars." (Introduction)
- Target **GGD 27-MM1 (IRAS 18162-2048)**: coordinates _not stated_; z/distance 1.4 kpc (range 1.2-1.4 kpc)  
  > "The HH 80–81 objects (at a distance of 1.4 kpc; see Appendix)" (Introduction); distance from Gaia DR2 YSO parallaxes plus STILISM extinction maps (this paper, Appendix)  
  > "The HH 80–81 objects (at a distance of 1.4 kpc; see Appendix)" (Introduction)

## Data provenance

- ALMA projects: 2015.1.00480.S
- bands: Band 6 (1.14 mm continuum); Band 7 for molecular lines  
  > "The ALMA#2015.1.00480.S project had also a science goal at Band 7 to observe several molecular lines in the 298-302 and 310-313 GHz frequency ranges (c40-6 configuration)." (ALMA Observations)
- frequencies and spectral setup: Band 6 TDM continuum, 253.0-257.0 and 269.0-273.0 GHz  
  > "The Band 6 receiver with the correlator set in continuum mode (time division mode, TDM) covering the 253.0-257.0 GHz and 269.0-273.0 GHZ frequency ranges was used." (ALMA Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: 37 antennas, c36-8/7 (Band 6)  
  > "The observations were carried out with 37 antennas in the c36-8/7 configuration" (ALMA Observations)
- baselines: 82 m to 11.05 km (13 to 5400 kλ)  
  > "which provided baselines between 82 m and 11.05 km (13 to 5400 k$\lambda$)." (ALMA Observations)
- angular resolution: 45.0 mas x 38.3 mas (continuum); 0.21'' x 0.16'' (lines)  
  > "The resulting synthesized beam has a full width at half maximum (FWHM) of 45.0 mas $\times$ 38.3 mas (PA = -62.4$\ensuremath{^\circ}$)." (ALMA Observations)
- max recoverable scale: _not stated_
- sensitivity: continuum rms 60 µJy/beam; line rms 1.3 mJy/beam per channel  
  > "The Stokes $I$ rms noise is 60  $\mu$Jy beam$^{-1}$." (ALMA Observations); "The rms noise achieved was 1.3 mJy beam$^{-1}$ per channel." (ALMA Observations)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: SO2 9(2,8)-8(1,7) (not stated)
- Line: SO2 19(3,17)-19(2,18) (not stated)
- Other facility **Gaia DR2**: parallaxes of YSOs for distance estimate  
  > "The two approaches rely on the Gaia DR2 catalogue" (The distance to the LDN 291 cloud)
- Other facility **STILISM**: 3D extinction maps vs distance  
  > "The second approach is to use the on-line *STILISM*[^1] application" (The distance to the LDN 291 cloud)
- External data: Near-IR polarimetric YSO catalogue used with Gaia  
  > "Figure [13](#fig:YSO) shows the polarization fraction as a function of the Gaia DR2 parallax for the YSOs in GGD 27 (from the (cite: Kwon16)" (Method 1) [from (cite: Kwon16)]
- External data: Disk flux density 351.30 ± 0.33 mJy and Td=109 K optically thin mass ~0.5 Msun  
  > "obtaining a flux density of 351.30 $\pm$ 0.33 mJy and a peak intensity of 46 mJy beam$^{-1}$  (cite: Busquet2019)" (4 The GGD 27-MM1 disk-jet system) [from (cite: Busquet2019)]
- External data: Jet mass-loss rate ~1e-5 Msun/yr at 1.7 kpc  
  > "They obtain a mass-loss rate of $\dot{M}_{\mathrm{out}}$ $\sim$10$^{-5}$  $M_{\ensuremath{\odot}}$ yr$^{-1}$  for a distance of 1.7 kpc" (4 The GGD 27-MM1 disk-jet system) [from (cite: CarrascoGonzalez2012)]
- External data: Bolometric luminosity ~2.0e4 Lsun at 1.7 kpc  
  > "The observed value is $\sim$2.0 $\times 10^{4}~L_{\odot}$ for a distance of 1.7 kpc (cite: Gomez2003)." (4 The GGD 27-MM1 disk-jet system) [from (cite: Gomez2003)]

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

- task: CASA tclean  
  > "This was done using the CASA task *tclean* with a value of 0.5 for the robust Briggs weighting parameter." (ALMA Observations)
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0.5 (continuum); natural weighting (line cubes); robust 1 for compact-source images  
  > "Velocity channel maps were obtained (after continuum subtraction) using *tclean* with natural weighting" (ALMA Observations)
- uv taper: only baselines >300 kλ used for disk image  
  > "we used visibilities from baselines larger than 300 k$\lambda$ (cite: Girart2018april)" (ALMA Observations)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: compact source removed from visibilities; line cubes continuum-subtracted after self-calibration  
  > "The Stokes $I$ image toward GGD 27 -MM1 was generated using the resulting visibilities after the subtraction of the compact source" (ALMA Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 45.0 x 38.3 mas, PA -62.4 deg  
  > "The resulting synthesized beam has a full width at half maximum (FWHM) of 45.0 mas $\times$ 38.3 mas (PA = -62.4$\ensuremath{^\circ}$)." (ALMA Observations)
- final rms: 60 µJy/beam  
  > "The Stokes $I$ rms noise is 60  $\mu$Jy beam$^{-1}$." (ALMA Observations)

### Inherited from earlier work

- Use of baselines >300 kλ to filter envelope emission  
  > "we used visibilities from baselines larger than 300 k$\lambda$ (cite: Girart2018april)" (ALMA Observations) [from (cite: Girart2018april)]
- Dynamical mass from PV diagrams by fitting Keplerian profile to 5-sigma contour  
  > "we followed the procedure given by (cite: Seifried16). This procedure fits the Keplerian profile to the 5-$\sigma$ contour emission" (4 The GGD 27-MM1 disk-jet system) [from (cite: Seifried16)]
- Disk model code (irradiated alpha-accretion disk)  
  > "The disk was modeled using the irradiated $\alpha$-accretion disk models created by (cite: D’Alessio1998; D’Alessio1999; D’Alessio2001; D’Alessio2006)" (3 Disk model) [from (cite: D’Alessio1998; D’Alessio1999; D’Alessio2001; D’Alessio2006)]

### Not stated but needed to reproduce (our reading)

- D'Alessio disk code is not public (provided privately); no access path stated
- Pixel size and image size for tclean
- Clean threshold, masks and iterations
- Self-calibration solint and line-free channels for line data
- Exact simutil/simobserve configuration for synthetic visibilities
- Calibration pipeline, CASA version and flux calibrator
- Phase-center coordinates of the target
- How the compact source was subtracted from visibilities in detail
- chi2 definition (noise weighting) and grid search ordering

## Analysis recipe

1. **Image continuum and remove compact central source**: Gaussian fits in image and visibility planes with min uv radius 3500-4750 kλ; compact source subtracted from visibilities before tclean imaging  
  > "A two dimensional Gaussian fit was performed to the different images obtained with different baseline ranges." (2.1 The compact source)
   - software: CASA
   - parameter: robust = 1 for compact-source images; robust 0.5, uv>300 kλ for disk image  
  > "with a robust weighting of 1" (2.1 The compact source)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive dynamical mass from SO2 PV diagrams**: PV cuts along PA 113 deg, Keplerian fit to 5σ contour following Seifried16  
  > "centered at the dust peak intensity with a position angle of 113$\ensuremath{^\circ}$, i.e. along the major axis of the disk" (4 The GGD 27-MM1 disk-jet system)
   - software: CASA
   - assumption: Keplerian rotation, inclination-corrected  
  > "assuming that they behave as a rotationally-supported disk (i.e., Keplerian velocity)" (4 The GGD 27-MM1 disk-jet system)
   - fitting: _not stated_
   - validation: procedure tested on synthetic PV maps from MHD simulations (Seifried16)  
  > "was tested in synthetic ALMA molecular line PV maps generated from MHD simulations for disks around both low- and high-mass stars" (4 The GGD 27-MM1 disk-jet system)
3. **Fit disk model grid to 1.14 mm image**: Grid of D'Alessio models; synthetic visibilities from model images with simutil, imaged with tclean with the same parameters; best fit chosen by visual inspection of radial profiles then minimum chi2 of residual map within R=230 au  
  > "then, from among this first selection we chose the best fit model based on minimum $\chi^2$ of the residual map" (5 The model-fitting procedure)
   - software: CASA, simutil, tclean, MIRIAD
   - parameter: Grid: M* 15-25 Msun, Teff 12000-18000 K, R* 10-30 Rsun, Macc 1e-5 to 2e-4 Msun/yr, Rdisk 130-250 au, Rin 10-20 au, i 44-54 deg, amax 100/500/1000 µm, alpha 0.1/0.01/0.001  
  > "Disk radius (au) | 130 – 250 | 10" (Table 1)
   - assumption: dust-to-gas 0.0065; two grain populations n(a)∝a^-3.5; Zbig=0.1H; mu=2.33; distance 1.4 kpc  
  > "dust-to-gas ratio of 0.0065 corresponding to the measured abundances of silicates and graphites in the ISM" (3 Disk model)
   - fitting: _not stated_
   - validation: chi2 vs inclination, Rdisk, Rin, Macc with others fixed; residuals below 5% of peak  
  > "The four parameters show a minimum at the value of our best fit model." (Model robustness)
4. **Fit power laws to model structure and test stability**: Minimum mean squared error power-law fits to Sigma(R) and Tc(R); Toomre Q computed from model  
  > "using the method of the minimum mean squared error (MSE)" (6 Results)
   - software: Python
   - fitting: _not stated_
   - validation: comparison with Kuiper & Hosokawa 2018 simulations  
  > "Our model shows very similar results in terms of disk mid-plane temperature and disk’s aspect ratio to this model" (7.3 Stability of the disk)
5. **Distance estimate**: Weighted mean Gaia DR2 parallax of YSOs and sigmoid fit to STILISM E(B-V) vs distance  
  > "We used a reduced $\chi^2$ fit. The distance for the large jump is $1270\pm65$ pc." (Method 2)
   - software: STILISM
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : imaging, simutil synthetic visibilities, tclean  
  > "The fitting procedure and analysis was done using Common Astronomy Software Applications (CASA)" (5 The model-fitting procedure)
- **MIRIAD** : data reduction/analysis  
  > "Multichannel Image Reconstruction, Image Analysis, and Display (cite: Sault95) data reduction software packages." (5 The model-fitting procedure)
- **D'Alessio disk models** : irradiated alpha-accretion disk structure  
  > "We are grateful to Nuria Calvet for making D’Alessio’s code available to us" (Acknowledgments)
- **STILISM** : 3D extinction maps  
  > "CASA (cite: McMullin2007), MIRIAD (cite: Sault95), PYTHON, STILISM" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Disk mass | 5 | not stated | Msun | 3 | $M_{\mathrm{disk}}$ ($M_{\odot}$) / 5 / calculated |
| Disk radius | 168 | not stated | au | 3 | $R_{\mathrm{disk}}$ (au) / 168 / adopted/refined |
| Mass accretion rate | 7e-5 | not stated | Msun/yr | 3 | resulted to be $\sim$ 7 $\times 10^{-5}$  $M_{\ensuremath{\odot}}$ yr$^{-1}$ |
| Dynamical mass SO2 9-8 | 31 | ±1 | Msun | 2 | yielded an inclination corrected dynamical mass of 31$\pm$1 and 21$\pm$1 |
| Dynamical mass SO2 19-19 | 21 | ±1 | Msun | 2 | yielded an inclination corrected dynamical mass of 31$\pm$1 and 21$\pm$1 |
| Compact source flux density | ~19 | not stated | mJy | 1 | show an unresolved source with a flux density of $\sim$19 mJy at the center of the disk |
| Distance (YSO Gaia) | 1248 | ±166 | pc | 5 | Therefore, the distance to the YSO cluster is 1248$\pm$166 pc. |
| Distance (extinction jump) | 1270 | ±65 | pc | 5 | The distance for the large jump is $1270\pm65$ pc. |
| Disk optical depth at 1.14 mm | 50 to 170 | not stated | dimensionless | 3 | with $\tau = \Sigma \chi$ ranging from 50 to 170 |
| Toomre stable radius | ~100 | not stated | au | 4 | The stability condition ($Q>1$) is satisfied up to a radius $R_{\mathrm{disk}}\sim100$ au. |

## Qualitative findings

- Disk is optically thick, warm (150-1400 K), flared; water snow line near disk edge (~170 au)  
  > "we estimate that the water snow line would be located near the edge of the disk, at a radius of $\sim$ 170 au" (7.5 Temperature distribution)

## Claim tuples

- H: Low-mass-star alpha-disk models can fit the GGD 27-MM1 disk | E: Grid of D'Alessio models fitted to the 1.14 mm image | R: Best fit Mdisk~5 Msun, Rdisk~170 au, i=49 deg, Macc~7e-5 Msun/yr | F: Disk is massive, compact, and consistent with dynamical mass | **supported**
- H: The disk is gravitationally stable | E: Toomre Q from best model | R: Q>1 up to ~100 au | F: Stable in inner part | **partially**
- H: Distance is smaller than 1.7 kpc | E: Gaia DR2 YSOs and STILISM | R: 1.2-1.4 kpc | F: Source distance 1.2-1.4 kpc | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Models successfully used for low- and intermediate-mass disks applied to test extrapolation to massive stars  
  > "we analyze the GGD 27–MM1 disk by applying models that have successfully explained disks around low-mass stars" (Introduction)
- Alternative: One-dust-population models require disk masses comparable to stellar mass, inconsistent with dynamical mass  
  > "indicating that at least two dust populations are needed to fit the observations" (7.2 Restrictions from polarization)
- How they decided it was enough: _not stated_
- Limitation (authors): Mass accretion rate poorly constrained by jet-based estimates; residuals significant beyond 150 au  
  > "Even though the mass accretion rate is not well determined using these methods" (4 The GGD 27-MM1 disk-jet system)
- Caveat (inferred, ours): Model fit by coarse grid and visual inspection, no formal uncertainties or MCMC
- Caveat (inferred, ours): Parameter degeneracies (alpha, Macc, grain settling) only partly explored
- Caveat (inferred, ours): Dynamical mass from only two SO2 lines at modest resolution
- Caveat (inferred, ours): Compact source subtraction may bias disk image

## Reproducibility

- Data public (paper): ALMA project code given; data from archive  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00480.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: D'Alessio disk code access
- Missing: Imaging details (cell, size, masks)
- Missing: Calibration details and version
- Missing: Compact-source removal procedure
- Data volume (inferred): ~50-200 GB for Band 6 and Band 7 measurement sets
- Score (inferred): 3/5, Public data and clear grid, but proprietary model code and missing imaging/calibration details.
- Rediscovery candidate: no, Requires non-public disk model code and the recipe is incomplete.

## Links

- Method: (cite: D’Alessio2006) (disk model description)
- Method: (cite: Seifried16) (Keplerian PV fitting for dynamical mass)
- Companion: (cite: Girart2018april) (original ALMA observations and polarization of the disk)
- Companion: (cite: Busquet2019) (disk flux density and mass estimate)
- Related: Gaia DR2
- Related: STILISM

## Checks

```json
{
 "quotes": 63,
 "quotes_ok": 63,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 78,
  "stated": 45,
  "rate": 0.577
 },
 "evidence_ok": true
}
```
