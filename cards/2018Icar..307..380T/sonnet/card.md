# Spatial variations in Titan's atmospheric temperature: ALMA and Cassini comparisons from 2012 to 2015

`2018Icar..307..380T` | Icarus 2018 | first author: Thelen, Alexander E. | arXiv: 1809.10891 | DOI: 10.1016/j.icarus.2017.10.042

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: solar_system
- Question: How does Titan's atmospheric temperature vary spatially and seasonally from 2012-2015, as retrieved from CO emission lines in ALMA flux-calibration data, and how does it compare with Cassini CIRS and radio occultation results?  
  > "Here we present the first spatially resolved temperature measurements of Titan obtained using ground-based radio observations." (Introduction)
- Target **Titan**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00724.S, 2012.1.00688.S, 2012.1.00501.S, 2012.1.00317.S
- bands: CO (6-5), (2-1), (3-2), (2-1) lines in 2012-2015 datasets  
  > "CO (3–2) | 15 Jun 2014 | 345.796 | 157 | 36 | 976" (Table 1)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: beams 0.35x0.28'' to 0.39x0.34'' (2012, 2014, 2015); 1.54x0.77'' in 2013  
  > "we extract spectra from 3 separate regions on Titan’s disk using datasets with beam sizes ranging from $0.35\times0.28''$ to $0.39\times0.34''$" (abstract)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 236 s (2012), 157 s (2013-2015)  
  > "CO (2–1) | 27 Jun 2015 | 230.538 | 157 | 42 | 976 | 0.37$''$ $\times$ 0.32$''$ | 2012.1.00317.S" (Table 1)
- observing dates: 05 Jun 2012, 14 Dec 2013, 15 Jun 2014, 27 Jun 2015  
  > "CO (2–1) | 14 Dec 2013 | 230.538 | 157 | 28 | 122 | 1.54$''$ $\times$ 0.77$''$ | 2012.1.00688.S" (Table 1)
- pi or archival as stated: Public archival flux-calibration observations of Titan  
  > "Titan is often used as a flux calibrator for ALMA science targets" (Observations)
- Line: CO 6-5 (691.473 GHz)
- Line: CO 3-2 (345.796 GHz)
- Line: CO 2-1 (230.538 GHz)
- Other facility **Cassini CIRS**: Nadir temperature maps (T84, T98, T100, T112) for a priori and comparison  
  > "we elected to extract similar data from CIRS nadir maps taken during the T84, T98, T100, and T112 flybys of Titan" (Cassini Comparisons)
- Other facility **Cassini radio occultation / Huygens HASI**: Tropospheric temperature profiles for a priori and comparison  
  > "Interpolating the HASI (cite: fulchignoni_05) and *Cassini* radio occultation science measurements from the T27, T31, T46, and T57 flybys" (Cassini Comparisons)
- External data: Radio occultation temperature profiles  
  > "temperature profiles of Titan’s lower atmosphere obtained by *Cassini* radio occultation science ((cite: schinder_12)" (Spectral Modeling and Results) [from (cite: schinder_12)]
- External data: CO abundance of 49.6 ppm  
  > "with a constant CO abundance of 49.6 ppm as found by (cite: serigano_16)" (Spectral Modeling and Results) [from (cite: serigano_16)]
- External data: N2 and CH4 vertical profiles  
  > "N$_2$ and CH$_4$ vertical profiles from (cite: niemann_10) and (cite: teanby_13)" (Spectral Modeling and Results) [from (cite: niemann_10); (cite: teanby_13)]
- External data: Line parameters from HITRAN 2012 and CDMS  
  > "We obtained spectral line parameters from the HITRAN 2012 and CDMS databases (cite: rothman_13; muller_01)" (Spectral Modeling and Results) [from (cite: rothman_13; muller_01)]
- Simulation/model as data: Butler-JPL-Horizons 2012 Titan flux model used for initial flux scale  
  > "We obtained initial flux density estimates by using the Butler-JPL-Horizons 2012 Titan flux model in the CASA reduction scripts" (Observations)

## Processing

### Calibration

- pipeline or manual: Modified JAO scripts re-run to retain CO lines  
  > "We processed data using modified versions of the scripts provided by the Joint ALMA Observatory, which often flag out strong lines in Titan’s atmosphere (such as CO)." (Observations)
- casa version: CASA 4.7.0  
  > "We re-ran these scripts in the NRAO’s CASA software package 4.7.0" (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Butler-JPL-Horizons 2012 Titan model  
  > "Butler-JPL-Horizons 2012 Titan flux model in the CASA reduction scripts, which is expected to be accurate to within 5$\%$" (Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA clean  
  > "Imaging was completed using the CASA `clean` task." (Observations)
- deconvolver: Högbom  
  > "Deconvolution of the ALMA point-spread function was performed by using the Högbom algorithm" (Observations)
- weighting robust: natural  
  > "with natural visibility weighting" (Observations)
- uv taper: _not stated_
- cell size: 0.03'' x 0.03''  
  > "The image pixel sizes were set to 0.03$''\times$0.03$''$." (Observations)
- image size: _not stated_
- masking: flux threshold of twice the expected RMS (typically ~15 mJy)  
  > "an flux threshold of twice the expected RMS noise (typically on order 15 mJy)" (Observations)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.35x0.28'' (2012), 1.54x0.77'' (2013), 0.39x0.34'' (2014), 0.37x0.32'' (2015)  
  > "0.37$''$ $\times$ 0.32$''$" (Table 1)
- final rms: _not stated_

### Inherited from earlier work

- Data reduction approach  
  > "We completed data reduction in a fashion similar to previous ALMA studies of Titan" (Observations) [from (cite: cordiner_14; cordiner_15; serigano_16; molter_16; palmer_17)]
- Spectral line parameters  
  > "as in (cite: serigano_16; molter_16)" (Spectral Modeling and Results) [from (cite: serigano_16; molter_16)]
- Conversion to spectral radiance units  
  > "as described by (cite: teanby_13)" (Spectral Modeling and Results) [from (cite: teanby_13)]
- Field-of-view averaging points  
  > "as detailed in Appendix A of (cite: teanby_13)" (Spectral Modeling and Results) [from (cite: teanby_13)]

### Not stated but needed to reproduce (our reading)

- Line-free/continuum channel ranges used for scaling
- Exact extraction regions (positions, sizes) of North/Center/South beam footprints
- Scaling factor values per dataset
- Targeted ALMA data member IDs / execution blocks
- NEMESIS version and retrieval configuration files
- Which a priori profiles were used exactly for each year
- Whether ALMA flux scale adopted in archive pipeline was reprocessed per scheduling block

## Analysis recipe

1. **Calibrate and image Titan data**: Modified JAO scripts in CASA, clean with Högbom, natural weighting, Doppler shift to Titan rest frame  
  > "Image spectral coordinates were Doppler-shifted to Titan’s rest frame using Topocentric radial velocities from JPL Horizons ephemerides." (Observations)
   - software: CASA
   - parameter: pixel 0.03'', threshold 2x RMS  
  > "The image pixel sizes were set to 0.03$''\times$0.03$''$." (Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract disk-averaged and regional spectra**: Extract flux over solid disk plus atmosphere plus 2-sigma_PSF; three regions North/Center/South with minimal beam overlap  
  > "We chose to model spectra from 3 regions (hereafter referred to as ‘North’, ‘Center’, and ‘South’) chosen to be as independent as possible" (Observations)
   - parameter: Titan radius 2575 km plus 1200 km atmosphere  
  > "extracting flux over Titan’s solid disk (2575 km), plus its extended atmosphere (1200 km)" (Observations)
   - fitting: _not stated_
   - validation: _not stated_
3. **Scale spectra to model continuum**: Constant multiplicative scaling factor (<5%) per spectrum from offsets between data and model continuum, line wings and core  
  > "A constant scaling factor was determined for each spectrum by averaging offsets between measurements of data and model continuum, CO line wings, and line core regions" (Spectral Modeling and Results)
   - fitting: _not stated_
   - validation: Scaling within errors of Butler-JPL-Horizons 2012 model for CO lines  
  > "ensured that flux density scaling factors were within the errors of the Butler-JPL-Horizons 2012 model for CO lines" (Spectral Modeling and Results)
4. **Retrieve disk-averaged temperature profiles**: NEMESIS line-by-line optimal estimation with 37-44 field-of-view averaging points; a priori from CIRS/Huygens, isothermal 160 K above 600 km  
  > "Upper atmospheric temperatures (\>600 km) were held as isothermal at 160 K." (Spectral Modeling and Results)
   - software: NEMESIS
   - parameter: 5 K a priori errors, correlation length 1.5 scale heights  
  > "with 5 K errors set on the *a priori* temperature profile; combined with a correlation length of 1.5 scale heights" (Spectral Modeling and Results)
   - assumption: Constant CO abundance of 49.6 ppm  
  > "with a constant CO abundance of 49.6 ppm as found by (cite: serigano_16)" (Spectral Modeling and Results)
   - fitting: Optimal estimation (NEMESIS)  
  > "We retrieve vertical temperature profiles by allowing NEMESIS to vary temperature measurements continuously throughout the atmosphere" (Spectral Modeling and Results)
   - validation: Comparison with CIRS and radio occultation  
  > "To validate our model of Titan’s atmosphere and the retrieved temperature profiles" (Cassini Comparisons)
5. **Retrieve spatially resolved profiles**: Use disk-averaged profiles as a priori; troposphere a priori from Cassini radio/HASI convolved with ALMA beam (2014, 2015)  
  > "We proceeded to use disk-averaged measurements as *a priori* temperature profiles to model spatially resolved spectra" (Spectral Modeling and Results)
   - software: NEMESIS
   - fitting: _not stated_
   - validation: _not stated_
6. **Compare with Cassini**: Two-sample KS test of retrieved profiles vs CIRS and radio occultation at <100 km  
  > "applying a two-sample Kolmogorov-Smirnov (KS) test to the temperature profiles presented here" (Cassini Comparisons)
   - fitting: _not stated_
   - validation: alpha>0.10 means not significant  
  > "do not seem statistically significant (i.e. $\alpha$\>0.10)" (Cassini Comparisons)

## Software

- **CASA** 4.7.0: Calibration and imaging  
  > "We re-ran these scripts in the NRAO’s CASA software package 4.7.0" (Observations)
- **NEMESIS** : Radiative transfer and temperature retrieval  
  > "radiative transfer modeling using the Non-Linear Optimal Estimator for Multivariate Spectral Analysis (NEMESIS) software package in line-by-line mode" (Spectral Modeling and Results)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Stratopause (~320 km) warming in northern latitudes 2012-2015 | 5 | not stated | K | 5 | We measure the stratopause (320 km) to increase in temperature by 5 K in northern latitudes from 2012–2015 |
| Latitudinal temperature variation | up to 15 | not stated | K | 5 | temperature profiles are found to consistently vary with latitude in all three years by up to 15 K |
| ALMA cooler than radio occultation, 50-100 km | up to 10 | not stated | K | 6 | We obtain temperature profiles that are cooler than interpolated radio occultation measurements by up to 10 K |
| KS D, disk-averaged 2014 vs CIRS | 0.27 (alpha 0.74) | not stated | dimensionless | 6 | / 2014               / 0.16    / 0.88         / 0.27 / 0.74     / |
| Largest temporal variation at ~120 km, north, 2012-2014 | 7 | not stated | K | 5 | We observe the largest temporal temperature variation of all profiles presented here, 7 K, from 2012–2014 at $\sim$ 120 km |

## Qualitative findings

- Disk-averaged profiles are nearly constant 2012-2015, while spatially resolved regions show seasonal changes in stratosphere and mesosphere  
  > "Disk-averaged temperature profiles stay relatively constant from year to year" (abstract)

## Claim tuples

- H: CO lines in ALMA flux-calibration data can retrieve spatially resolved temperature profiles consistent with Cassini | E: NEMESIS retrievals for three regions compared to CIRS and radio occultation with KS tests | R: Deviations mostly <5 K; KS alpha>0.10 | F: ALMA CO retrievals agree with Cassini within errors | **supported**
- H: Seasonal variation is detectable in resolved regions | E: Compare 2012, 2014, 2015 regional profiles | R: ~5 K stratopause warming in north; lower stratosphere changes | F: Titan's atmosphere responds to season, mostly at high latitudes, though often within errors | **partially**

## Reasoning

- Why this data: Frequent public Titan flux-calibration observations over ALMA's lifetime  
  > "allowing us to utilize frequent (almost daily for $\sim$7 months of the year) observations" (Observations)
- Why this method: _not stated_
- Alternative: CO abundances >20% from nominal gave poor fits or large temperature variations  
  > "Temperature retrievals obtained using CO abundances in excess of $20\%$ of the nominal value (49.6 ppm) resulted in poor spectral fits or large variations in temperature" (Spectral Modeling and Results)
- How they decided it was enough: _not stated_
- Limitation (authors): Short integration times and large beams limit temporal variation significance; latitudinal structure is dampened by beam weighting  
  > "limited by the short integration times of flux calibration datasets and large beam sizes" (Conclusions)
- Caveat (inferred, ours): Ad hoc flux scaling factors (<5%) can shift retrieved temperatures and are not tabulated
- Caveat (inferred, ours): Regional footprints span wide latitude ranges, limiting spatial claims
- Caveat (inferred, ours): KS test on profiles is weakly justified for correlated profile points
- Caveat (inferred, ours): 2013 data lacks spatial resolution

## Reproducibility

- Data public (paper): Public ALMA archive data; retrieved profiles and models posted online  
  > "We obtained public data of Titan from the ALMA science archive" (Observations)
- Products in archive: _not stated_
- Missing: NEMESIS configuration and a priori files
- Missing: Region definitions and scaling factor values
- Missing: Line-free channel selections
- Data volume (inferred): Small; four short Titan flux-calibration scheduling blocks, likely tens of GB raw
- Score (inferred): 3/5, Public data and a fairly clear recipe, but key retrieval inputs and scaling factors are unstated
- Rediscovery candidate: no, Retrieval needs NEMESIS setup and Cassini inputs not fully specified; results largely comparative figures.

## Links

- Method: (cite: irwin_08) (NEMESIS retrieval code)
- Method: (cite: teanby_13) (Spectral radiance conversion and FOV averaging)
- Companion: (cite: serigano_16) (Earlier ALMA disk-averaged Titan temperature retrievals, CO abundance)
- Related: Cassini CIRS
- Related: Cassini radio science

## Checks

```json
{
 "quotes": 63,
 "quotes_ok": 63,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 81,
  "stated": 47,
  "rate": 0.58
 },
 "evidence_ok": true
}
```
