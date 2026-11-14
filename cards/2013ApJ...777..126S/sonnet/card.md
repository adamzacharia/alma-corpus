# Luminous Infrared Galaxies with the Submillimeter Array. IV. <SUP>12</SUP>CO J = 6-5 Observations of VV 114

`2013ApJ...777..126S` | The Astrophysical Journal 2013 | first author: Sliwa, Kazimierz | arXiv: 1309.1144 | DOI: 10.1088/0004-637X/777/2/126

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, astrochemistry
- Question: What are the beam-averaged physical conditions (Tkin, nH2, N_CO, 12CO/13CO abundance) and the CO-to-H2 conversion factor of the molecular gas in VV 114E, using new SMA 12CO J=6-5 plus low-J CO data including ALMA 13CO J=1-0?  
  > "We use the radiative transfer code RADEX and a Bayesian likelihood code to constrain the temperature ($T_{\rm{kin}}$), density ($n_{\rm{H_{2}}}$) and column density ($N_{\rm{^{12}CO}}$) of the molecular gas." (abstract)
- Target **VV 114 (Arp 236, IC 1623)**: coordinates VV 114E CO 3-2 peak: 01h07m47.453s, -17d30m25.037s (J2000)  
  > "We model the molecular gas at the peak position of $^{12}$CO $J$=3-2 ($\alpha_{J2000}$ = 01$^{h}$07$^{m}$47.453$^{s}$, $\delta_{J2000}$ = -17$^{d}$30$^{m}$25.037$^{s}$) in VV 114E." (Section 5.3 Modeling Results); z/distance 86 Mpc  
  > "VV 114 (Arp 236, IC 1623, IRAS 01053-1746) is a nearby LIRG at a distance of 86 Mpc ($H_{o}$ = 70.5 km s$^{-1}$ Mpc$^{-1}$, $\Omega_{M}$ = 0.27, $\Omega_{\Lambda}$ = 0.73; 1$''$ = 417 pc)" (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00467.S
- bands: ALMA cycle 0 13CO J=1-0 (band not stated); SMA 690 GHz receiver for 12CO 6-5  
  > "VV 114 was observed with ALMA during cycle 0 in $^{13}$CO $J$=1-0 (Saito et al. in prep.) using the compact configuration." (2.2 Additional CO Data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: ALMA compact configuration (13CO 1-0)  
  > "using the compact configuration" (2.2 Additional CO Data)
- baselines: _not stated_
- angular resolution: 13CO J=1-0 beam 3.7 x 1.4 arcsec, rms 2 mJy/beam in 40 km/s channels  
  > "$^{13}$CO $J$=1-0$^{d}$ | 4.0 $\pm$ 0.3 | \- | \- | 3.7 $\times$ 1.4 | 2" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: ALMA 13CO 1-0 is archival, calibrated uv-data from the ALMA archive (Saito et al. in prep.)  
  > "We obtained calibrated $uv$-data from the ALMA archive." (2.2 Additional CO Data)
- Line: 13CO J=1-0 (not stated)
- Other facility **SMA**: New 12CO J=6-5 map; 12CO 2-1, 3-2 and 13CO 2-1 maps from Paper I  
  > "The $^{12}$CO $J$=6-5 emission in VV 114 was observed with the SMA on 2008 August 26 using a two-point mosaic." (2.1 12CO J=6-5 SMA Data)
- Other facility **JCMT**: 12CO 3-2 and 2-1 single-dish maps for short-spacing recovery  
  > "We recover the short spacings of the $^{12}$CO $J$=2-1 and $^{12}$CO $J$=3-2 SMA datasets using the JCMT datasets." (2.2 Additional CO Data)
- Other facility **OVRO**: 12CO J=1-0 cube (Yun et al. 1994)  
  > "We have obtained a natural weighted clean cube of $^{12}$CO $J$=1-0 observed with the Owens Valley Radio Observatory (OVRO) first published in Yun et al. (1994)." (2.2 Additional CO Data)
- Other facility **Herschel FTS**: Archival 12CO 6-5 total flux to estimate missing flux  
  > "we use an archival $Herschel$ FTS spectrum to estimate the missing flux." (4 12CO J=6-5 Emission)
- External data: OVRO 12CO J=1-0 map  
  > "OVRO map published in Yun et al. (1994)" (Table 1) [from Yun et al. (1994) (cite: 1994ApJ...430L.109Y)]
- External data: SMA 12CO 2-1, 3-2 and 13CO 2-1 uv-data  
  > "The calibrated $uv$-data from Paper I, in FITS format, were imported into CASA for further processing and imaging." (2.2 Additional CO Data) [from Wilson et al. 2008 (Paper I)]
- External data: Herschel FTS 12CO 6-5 flux 1390 +/- 100 Jy km/s  
  > "The total flux of the $^{12}$CO $J$=6-5 line is 1390 $\pm$ 100 Jy km s$^{-1}$ from the FTS spectrum (M.R.P. Schirm 2013, private communication)" (4 12CO J=6-5 Emission) [from M.R.P. Schirm 2013, private communication]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Calibrated ALMA uv-data obtained from the archive  
  > "We obtained calibrated $uv$-data from the ALMA archive." (2.2 Additional CO Data)
- flux calibrator: _not stated_
- flux scale uncertainty: 20%  
  > "The absolute flux scale was set using Uranus and checked using Callisto suggesting an accuracy level of the flux calibration of 20%." (2.1 12CO J=6-5 SMA Data)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Integrated intensity map using channels with emission, 2 sigma cutoff  
  > "We created an integrated intensity map with a 2$\sigma$ cutoff using velocity channels with emission from VV 114 (see Figure 1)." (2.2 Additional CO Data)
- multiscale scales: _not stated_
- continuum subtraction: uv continuum subtracted using line-free channels (ALMA data)  
  > "The $uv$-data were continuum subtracted using line-free channels and a 40 km s$^{-1}$ cleaned datacube was created." (2.2 Additional CO Data)
- line free channels: _not stated_
- primary beam correction: all integrated intensity maps corrected for primary beam  
  > "All integrated intensity maps were corrected for the primary beam." (2.2 Additional CO Data)
- array combination: _not stated_
- smoothing: All maps degraded with Gaussian taper to 6.5 x 3.7 arcsec  
  > "We applied a Gaussian taper to the observations to degrade the resolution." (3 Line Ratio Maps)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- SMA 12CO 2-1/3-2 observations, calibration and processing  
  > "The observations and calibration details are given in Paper I." (2.2 Additional CO Data) [from Wilson et al. (2008; Paper I)]
- Short-spacing feathering method  
  > "We use the the method of Paper III assuming the flux scales of both datasets to be the same." (2.2 Additional CO Data) [from Sliwa et al. 2012 (Paper III)]

### Not stated but needed to reproduce (our reading)

- ALMA 13CO J=1-0 weighting/robust, cell size, clean threshold and beam details
- ALMA calibration/CASA version
- line-free channels and velocity ranges
- feathering parameters
- Likelihood code is not public; observational uncertainties used per line
- Saito et al. in prep. for ALMA observation details

## Analysis recipe

1. **Make line-ratio maps**: Degrade all maps to 6.5x3.7 arcsec via Gaussian taper, convert to K km/s, divide maps with 2 sigma cutoff  
  > "We have degraded the resolution of all the maps to the resolution of the OVRO $^{12}$CO $J$=1-0 map, 6.5$''$ $\times$ 3.7$''$." (3 Line Ratio Maps)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **RADEX grid and Bayesian likelihood fit**: RADEX grids in Tkin, nH2, N12CO with 13CO grids; Bayesian likelihood code fits 12CO and 13CO line fluxes  
  > "The Bayesian likelihood code determines the most probable solutions for the physical conditions of the molecular gas by comparing the RADEX calculated and the observed $^{12}$CO and $^{13}$CO line fluxes." (5.2 Likelihood Analysis)
   - software: RADEX
   - parameter: Tkin 10^0.7-10^3.8 K, nH2 10^1-10^7 cm-3, N12CO 10^12-10^18 cm-2, dv=1 km/s; Grid 2 [12CO]/[13CO]=10-10^5  
  > "We also generate a second $^{13}$CO grid expanding the relative abundance to $^{12}$CO (\[$^{12}$CO\]/\[$^{13}$CO\] = 10 – 10$^{5}$; Grid 2)." (5.1 Radiative Transfer Model)
   - assumption: Priors: column mass below dynamical mass, column length below region size, 0<tau<100  
  > "The third prior constrains the optical depth to be 0 $<$ $\tau$ $<$ 100." (5.2 Likelihood Analysis)
   - fitting: Likelihood with 1DMax and 4DMax; four parameters Tkin, nH2, N12CO, filling factor  
  > "The likelihood code generates two calculated values for each parameter: the 1DMax and the 4DMax." (5.2 Likelihood Analysis)
   - validation: Compared Grid 1 and Grid 2 solutions  
  > "To see if hitting the upper limit of \[$^{12}$CO\]/\[$^{13}$CO\] affects our results, we use Grid 2 with the expanded range of values." (5.3 Modeling Results)
3. **Derive CO-to-H2 conversion factor**: Mass from 4DMax column density and xCO divided by 12CO J=1-0 luminosity; dynamical-mass upper limit  
  > "assuming a $^{12}$CO to H$_{2}$ abundance ratio of $x_{\rm{CO}}$ = 3 x 10$^{-4}$ (Ward et al. 2003), we can measure the CO-to-H$_{2}$ conversion factor" (6.3 CO-to-H2 Conversion Factor)
   - assumption: xCO = 3e-4  
  > "x_{\rm{CO}}$ = 3 x 10$^{-4}$ (Ward et al. 2003)" (6.3 CO-to-H2 Conversion Factor)
   - fitting: _not stated_
   - validation: Compared with Downes & Solomon 1998 and dynamical-mass upper limit  
  > "The upper limit is consistent with the radiative transfer model-derived value for $\alpha_{CO}$." (6.3 CO-to-H2 Conversion Factor)

## Software

- **CASA** : Imaging and processing of SMA and ALMA uv-data  
  > "The calibrated $uv$-data were converted to FITS format and then imported into CASA for further processing and imaging." (2.1 12CO J=6-5 SMA Data)
- **RADEX** : Radiative transfer line flux grids  
  > "we use the radiative transfer code RADEX (van der Tak et al. 2007)" (5.1 Radiative Transfer Model)
- **IDL MIR** : SMA data reduction  
  > "Data reduction was done with the IDL MIR package." (2.1 12CO J=6-5 SMA Data)
- **Starlink** : JCMT 12CO 2-1 cube  
  > "using the `Starlink` software (Currie et al. 2008)" (2.2 Additional CO Data)
- **APLpy** : Plotting  
  > "This research made use of APLpy, an open-source plotting package for Python" (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Tkin (4DMax, Grid 2) | 38 | 1sigma range 42-459 | K | 2 | $T_{\rm{kin}}$ (K) / 51 / 38 / 42 – 459 |
| [12CO]/[13CO] | 229 | 112-603 (1 sigma range) | dimensionless | 2 | / 229 / 229 / 112 – 603 |
| alpha_CO | 0.5 | +0.6/-0.3 | Msun (K km/s pc^2)^-1 | 3 | We measure $\alpha_{CO}$ to be 0.5$^{+0.6}_{-0.3}$ $M_{\odot}$ (K km s$^{-1}$ pc$^{2}$)$^{-1}$. |
| 13CO J=1-0 flux (ALMA) | 4.0 | 0.3 | Jy km/s | 1 | 4.0 $\pm$ 0.3 |
| 12CO 6-5 SMA flux | 150 | 40 | Jy km/s | 0 | The total flux of $^{12}$CO $J$=6-5 in the SMA map is 150 $\pm$ 40 Jy km s$^{-1}$. |

## Qualitative findings

- 12CO 6-5 detected only in VV 114E  
  > "The $^{12}$CO $J$=6-5 line is only detected in VV 114E (Figure 1 and 2)." (4 12CO J=6-5 Emission)

## Claim tuples

- H: What are the gas conditions in VV 114E? | E: RADEX plus Bayesian likelihood on CO SLED | R: Tkin=38 K, nH2=10^2.89 | F: Cold, moderately dense gas component | **supported**
- H: Is [12CO]/[13CO] enhanced? | E: Grid 2 likelihood | R: 229 | F: About three times the local ISM value, explaining the high line ratio | **supported**
- H: Is alpha_CO consistent with the ULIRG value? | E: Model column density and luminosity | R: 0.5 (+0.6/-0.3) | F: Agrees with Downes & Solomon 0.8 | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Grid 1 solution (hot 390 K, diffuse) rejected because abundance ratio hit grid upper limit  
  > "The most probable \[$^{12}$CO\]/\[$^{13}$CO\] value hit the upper limit of our grid" (5.3 Modeling Results)
- How they decided it was enough: _not stated_
- Limitation (authors): Missing flux in 6-5 SMA map ~89%; no high-resolution short-spacing data  
  > "we are missing 89 $\pm$ 10 $\%$ of the flux" (4 12CO J=6-5 Emission)
- Caveat (inferred, ours): Beam-averaged single-position modelling with only 6 line fluxes for 4-5 parameters
- Caveat (inferred, ours): Heterogeneous resolutions and missing flux in 6-5 may bias the SLED
- Caveat (inferred, ours): ALMA data role minor and not described in detail

## Reproducibility

- Data public (paper): ALMA calibrated data obtained from archive; SMA/OVRO data from earlier papers  
  > "We obtained calibrated $uv$-data from the ALMA archive." (2.2 Additional CO Data)
- Products in archive: _not stated_
- Missing: Likelihood code (Z-Spec team) availability
- Missing: Herschel FTS flux private communication
- Missing: ALMA imaging parameters
- Data volume (inferred): <10 GB for ALMA part
- Score (inferred): 3/5, Modeling recipe fairly detailed but likelihood code private and several inputs inherited or private.
- Rediscovery candidate: no, ALMA role minor; requires non-public code and multi-facility data.

## Links

- Method: van der Tak et al. 2007 (cite: 2007A&A...468..627V) (RADEX)
- Method: Kamenetzky et al. 2012; Rangwala et al. 2011 (Likelihood code details)
- Companion: Wilson et al. 2008 (Paper I) (SMA CO 2-1/3-2 data)
- Companion: Sliwa et al. 2012 (Paper III) (Same method applied to Arp 299)
- Related: SMA LIRG survey

## Checks

```json
{
 "quotes": 51,
 "quotes_ok": 51,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 40,
  "rate": 0.556
 },
 "evidence_ok": true
}
```
