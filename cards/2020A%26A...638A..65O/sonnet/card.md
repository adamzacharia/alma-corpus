# ALMA and VLA reveal the lukewarm chromospheres of the nearby red supergiants Antares and Betelgeuse

`2020A&A...638A..65O` | Astronomy and Astrophysics 2020 | first author: O'Gorman, E. | arXiv: 2006.08023 | DOI: 10.1051/0004-6361/202037756

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: stellar_physics, evolved_stars
- Question: Does the red supergiant Antares have a chromosphere detectable at radio wavelengths, and what are its temperature structure and spectral index from ALMA band 8 to VLA S band?  
  > "We first present spatially resolved ALMA and VLA continuum observations of the early-M red supergiant Antares to search for the presence of a chromosphere at radio wavelengths." (abstract)
- Target **Antares (alpha Sco A)**: coordinates _not stated_; z/distance 170 (+35/-25) pc  
  > "it is possible that Antares is the nearest RSG ($d=170^{+35}_{-25}\,$pc, (cite: van_Leeuwen_2007))" (Introduction); distance from van Leeuwen 2007  
  > "it is possible that Antares is the nearest RSG ($d=170^{+35}_{-25}\,$pc, (cite: van_Leeuwen_2007))" (Introduction)

## Data provenance

- ALMA projects: 2016.1.00234.S
- bands: ALMA bands 3, 4, 7, 8; VLA S, C, X, Ku, K, Ka, Q  
  > "Antares was observed with ALMA in four unique continuum bands (bands 3, 4, 7, and 8) between July and October 2017" (2 Observations and data reduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: 7.5 GHz effective bandwidth over four spectral windows per ALMA band  
  > "with 7.5 GHz effective bandwidth spread over four spectral windows in each of the bands" (2 Observations and data reduction)
- arrays: _not stated_
- configurations: VLA A configuration  
  > "Antares was observed with the VLA in the most extended A configuration" (2 Observations and data reduction)
- baselines: Band 3: 41 m-16.2 km; band 4: 41 m-12.1 km; bands 7 and 8: 17 m-3.7 km  
  > "using 45 antennas, with baselines ranging from 41 m to 16.2 km" (2 Observations and data reduction)
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 3-5 min per ALMA band; 18-49 min per VLA band  
  > "with only between 3 and 5 minutes spent on the target in each track" (2 Observations and data reduction)
- observing dates: ALMA Jul-Oct 2017; VLA Jun 2015-Dec 2016  
  > "between June 2015 and December 2016" (2 Observations and data reduction)
- pi or archival as stated: _not stated_
- Other facility **VLA**: Continuum at 2-50 GHz (S to Q bands)  
  > "bands S, C, X, Ku, K, Ka, and Q" (2 Observations and data reduction)
- Other facility **HST STIS/GHRS**: FUV spectra of Betelgeuse and ASTRAL E230M spectrum used for NLTE comparison  
  > "Space Telescope Imaging Spectrograph (STIS) of the HST (cite: carpenter_2018)" (4.2 NLTE modeling of the FUV radiation field)
- External data: Photospheric angular diameter of Antares 37.38 mas  
  > "where the diameter of the optical photosphere is 37.38 mas (cite: ohnaka_2013)" (3.3 Temperature profile of the atmosphere) [from (cite: ohnaka_2013)]
- External data: Betelgeuse ALMA/VLA temperature distribution used in revised thermodynamic model  
  > "based on the ALMA and VLA temperature distribution shown in Figure 2 of (cite: ogorman_2017)" (4.2 NLTE modeling of the FUV radiation field) [from (cite: ogorman_2017)]

## Processing

### Calibration

- pipeline or manual: Standard ALMA and VLA calibration pipelines, manually inspected  
  > "calibrated using standard ALMA and VLA calibration pipelines and manually inspected and imaged using CASA 4.7.2" (2 Observations and data reduction)
- casa version: CASA 4.7.2  
  > "calibrated using standard ALMA and VLA calibration pipelines and manually inspected and imaged using CASA 4.7.2" (2 Observations and data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1517-2422 (ALMA); 3C286 (VLA)  
  > "The quasar J1517-2422 from the ALMA quasar catalog served as both bandpass and absolute flux density calibrator" (2 Observations and data reduction)
- flux scale uncertainty: ALMA <10% bands 3,4,7, <15% band 8; VLA 5% S-Ku, 15% K, Ka, Q  
  > "less than 10% in bands 3, 4, and 7 and less than 15% in band 8" (2 Observations and data reduction)
- self calibration: Two to three rounds of phase and one round of amplitude self-calibration  
  > "two to three rounds of phase self-calibration and one round of amplitude self-calibration" (2 Observations and data reduction)

### Imaging

- task: CLEAN, MFS, nterms=2  
  > "with the multifrequency synthesis mode, two Taylor coefficients to model the frequency dependence" (2 Observations and data reduction)
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0  
  > "Briggs weighting with a robust parameter of 0" (2 Observations and data reduction)
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

### Not stated but needed to reproduce (our reading)

- Cell size, image size, masks and clean thresholds
- UVMULTIFIT starting parameters and fitting settings
- Which VLA spectral windows were flagged
- Details of the HII-region model used for subtraction
- Final NLTE model of Betelgeuse is unpublished ('presented elsewhere')
- Coordinates of target and phase centre

## Analysis recipe

1. **Remove HII region emission**: Model the ionized region with CLEAN, Fourier transform with FT, subtract with UVSUB at S, C, X bands  
  > "Finally, the UVSUB task was used to subtract this model from the actual visibilities to leave a dataset containing only the visibilities of Antares." (2 Observations and data reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit size, shape and flux in uv-plane**: Fit uniform-intensity circular disks (VLA) and elliptical disks (ALMA) with spectral index free to visibilities  
  > "Uniform-intensity elliptical disk models in which the flux density depended on frequency (i.e., a spectral index) were found to fit all of the four ALMA datasets best." (3.1 Size and shape of the Antares atmosphere)
   - software: UVMULTIFIT
   - fitting: _not stated_
   - validation: Residual images show no substantial residuals  
  > "because no substantial residuals are detected in any of the residual images, we are confident that our model represents the data well" (3.1 Size and shape of the Antares atmosphere)
3. **Derive temperature profile**: Brightness temperature from flux and diameter equals local gas temperature where optical depth ~1; plotted against radius  
  > "the brightness temperature is just the local gas temperature where the optical depth is near unity, averaged across the stellar disk" (3.3 Temperature profile of the atmosphere)
   - assumption: Optically thick thermal emission; photospheric diameter 37.38 mas  
  > "where the diameter of the optical photosphere is 37.38 mas (cite: ohnaka_2013)" (3.3 Temperature profile of the atmosphere)
   - fitting: _not stated_
   - validation: _not stated_
4. **MOLsphere optical depth**: Estimate H- opacity of MOLsphere from CO column density at 2000 K in chemical equilibrium  
  > "we obtained an optical depth of $1.3 \times 10^{-4}$ for the geometrical thickness of 0.3 R$_{\star}$" (7 Calculating the optical depth of the MOLsphere)
   - fitting: _not stated_
   - validation: _not stated_
5. **NLTE FUV continuum modelling of Betelgeuse**: Time-independent NLTE spherical radiative transfer for Si I, Fe I, C I, Mg I continua, with and without Lyα/Lyβ photoionization, compared with STIS radiation temperatures  
  > "we performed time-independent nonlocal thermal equilibrium (NLTE) spherical radiative transfer computations for the formation of the Si I continua" (4.2 NLTE modeling of the FUV radiation field)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7.2: Calibration, CLEAN imaging, FT, UVSUB  
  > "manually inspected and imaged using CASA 4.7.2" (2 Observations and data reduction)
- **UVMULTIFIT** : Direct fitting of uv-data  
  > "we analyzed the *uv*-data directly using the UVMULTIFIT code (cite: vidal_2014)" (2 Observations and data reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Antares diameter at 405 GHz (geometric mean) | 50.7 | not stated | mas | 2 | the star deceases in diameter from 68.4 mas (3.7 R$_{\star}$) at 97.5 GHz to 50.7 mas (2.7 R$_{\star}$) at 405 GHz |
| Diameter at 3 GHz | 430.7 | 9.1 | mas | 2 | $430.7\pm9.1$ |
| Spectral index above 20 GHz | 1.42 | not stated | dimensionless | 2 | below 8 GHz the spectral index value is 0.8, while above 20 GHz, the value rises to 1.42 |
| Gas temperature at 1.35 R* | 2682 | 400 | K | 3 | provides a measure of the gas temperature of 2682 $\pm$ 400 K |
| Peak gas temperature at 2.5 R* | 3777 | 567 | K | 3 | maximum value of 3777 $\pm$ 567 K at 2.5 R$_{\star}$ |
| Brightness temperature at 3 GHz | 1647 | 110 | K | 3 | $1647\pm 110$ |
| MOLsphere optical depth | 1.3e-4 | not stated | dimensionless | 4 | we obtained an optical depth of $1.3 \times 10^{-4}$ |

## Qualitative findings

- ALMA atmosphere is elongated (15% flattening) at similar position angle in all four bands  
  > "All four ALMA measurements show that the shape of the atmosphere is elongated, with a flattening of 15% at a similar position angle." (abstract)

## Claim tuples

- H: Antares has a chromospheric temperature rise detectable at radio wavelengths | E: Multi-frequency ALMA+VLA uv-plane disk fits and brightness temperatures | R: Tb rises from 2682 K at 1.35 R* to 3777 K at ~2.5 R*, then falls to 1647 K | F: A lukewarm chromosphere exists | **supported**
- H: Lukewarm temperature could be an average of hot and cool MOLsphere gas | E: Optical depth of MOLsphere with H- opacity | R: tau ~1e-4 | F: MOLsphere transparent; chromosphere is real | **supported**
- H: Hot UV-emitting plasma coexists | E: NLTE FUV modelling for Betelgeuse | R: Radio-temperature model underpredicts FUV; hot photoionization component needed | F: Hot (>7000 K) component with small filling factor exists | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Term 'radio photosphere' deemed unnecessary for RSGs since their radio properties differ from AGB stars  
  > "the inclusion of the term *radio photosphere* is unnecessary" (4.5 RSGs versus AGB stars at radio wavelengths)
- How they decided it was enough: _not stated_
- Limitation (authors): Beams comparable to stellar size, so properties derived from visibilities; small-scale structure needs higher resolution  
  > "ALMA continuum data with higher spatial resolution are required to detect such features" (6 Searching for small-scale asymmetries)
- Caveat (inferred, ours): Model-dependent uniform disk fits give very small formal errors
- Caveat (inferred, ours): Brightness temperature equals gas temperature assumes tau~1 and optically thick
- Caveat (inferred, ours): Epochs differ between bands over two years
- Caveat (inferred, ours): NLTE model not fully published

## Reproducibility

- Data public (paper): ALMA project code given; ALMA data acknowledged via ADS/JAO  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00234.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Imaging parameters beyond robust=0
- Missing: UVMULTIFIT setup
- Missing: Unpublished Betelgeuse NLTE model
- Data volume (inferred): ~50-150 GB for the four ALMA tracks plus VLA
- Score (inferred): 6/5, Public data and clear fitting approach with tabulated results, but missing fitting setup details.
- Rediscovery candidate: yes, Public data, uv-fits and tabulated numeric results (diameters, flux densities, temperatures) can be redone.

## Links

- Method: (cite: vidal_2014) (UVMULTIFIT uv-fitting code)
- Companion: (cite: ogorman_2017) (Betelgeuse ALMA/VLA study)

## Checks

```json
{
 "quotes": 45,
 "quotes_ok": 45,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 68,
  "stated": 33,
  "rate": 0.485
 },
 "evidence_ok": true
}
```
