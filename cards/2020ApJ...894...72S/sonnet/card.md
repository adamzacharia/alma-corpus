# Atacama Compact Array Measurements of the Molecular Mass in the NGC 5044 Cooling-flow Group

`2020ApJ...894...72S` | The Astrophysical Journal 2020 | first author: Schellenberger, Gerrit | arXiv: 2004.01717 | DOI: 10.3847/1538-4357/ab879c

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: galaxy_clusters_and_sz, nearby_galaxies, star_formation
- Question: How much molecular gas is in NGC 5044, how is it distributed in clouds and on which scales, and where are the absorbing clouds relative to the AGN, using ACA 7m+TP CO(2-1) data  
  > "We demonstrate, using the 7m array data, that we can recover the total flux inferred from IRAM 30m single dish observations, which corresponds to a total molecular mass of about $\SI{4e7}{M_\odot}$." (abstract)
- Target **NGC 5044**: coordinates _not stated_; z/distance 31.2 Mpc; v_sys = 2757 km/s  
  > "We adopt a systemic velocity of $\SI{2757}{km\,s^{-1}}$ (heliocentric) for NGC 5044 and a luminosity distance of $\SI{31.2}{Mpc}$ ((cite: Tonry2001-wi))" (Introduction); distance from Tonry et al. 2001  
  > "We adopt a systemic velocity of $\SI{2757}{km\,s^{-1}}$ (heliocentric) for NGC 5044 and a luminosity distance of $\SI{31.2}{Mpc}$ ((cite: Tonry2001-wi))" (Introduction)

## Data provenance

- ALMA projects: 2011.0.00735.S, 2016.1.00533.S, 2016.2.00134.S, 2017.1.00784.S
- bands: Band 6; four 185 MHz spectral windows  
  > "All ACA and ALMA observations were configured to provide four spectral windows within Band 6, each with a bandwidth of $\SI{185}{MHz}$." (2.1 7m array)
- frequencies and spectral setup: CO(2-1) at 228.397 GHz; other SPWs 226.418, 242.314, 244.244 GHz  
  > "The central frequencies for the other three spectral windows were $\SI{226.418}{GHz}$, $\SI{242.314}{GHz}$, and $\SI{244.244}{GHz}$." (2.1 7m array)
- continuum bandwidth: _not stated_
- arrays: ALMA 12m (cycle 0 and 4), ACA 7m, ACA total power  
  > "NGC 5044 was observed in cycle 4 with two different ALMA configurations (compact and extended) and with the ACA (7m array plus antennae for total power measurements)." (2 ALMA Data Reduction)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 7m beam 6.9x5.1 arcsec; TP 28.4 arcsec  
  > "6.9 x 5.1" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: rms 1.8 mJy/beam (7m), 12 (TP) in 10 km/s channels  
  > "rms ($\si{mJy\,bm^{-1}}$) | 1.4 | 0.49 | 1.8 | 0.47 | 12" (Table 1)
- time on source: 7m 306 min; TP 614 min; 12m extended 44 min  
  > "Time (min) | 29 | 44 | 306 | 48 | 614" (Table 1)
- observing dates: 7m 2016 July; TP Oct-Dec 2018  
  > "Date | 2012 Jan 13 | 2017 Aug 3 | 2016 July | 2016 Nov 15 | 2018 Oct – Dec" (Table 1)
- pi or archival as stated: _not stated_
- Line: CO 2-1 (230.538 GHz)
- Other facility **IRAM 30m**: single-dish CO(2-1) spectrum for flux comparison  
  > "the bulk of the CO(2-1) emission in NGC 5044 arises from diffuse molecular structures" (3)
- Other facility **MUSE**: Halpha image and velocity map  
  > "NGC 5044 was observed with MUSE in four nights from Jan. 17, 2015 to Feb. 3, 2015" (4.1.2)
- External data: Cycle 0 ALMA cloud catalog (24 clouds)  
  > "has been analyzed by (cite: David2014-jn) who detected 24 clouds" (3.5) [from (cite: David2014-jn)]
- External data: Hot gas density model and temperature 0.8 keV  
  > "We adapt the power-law model of the hot gas density distribution from Eq. (2) in (cite: David2017-ig)" (4.2) [from (cite: David2017-ig)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline scripts for 7m; phase self-cal  
  > "The 7m data were calibrated with CASA version 4.7.2 ((cite: McMullin2007-ed)) using the ALMA pipeline scripts, but CASA version 5.4.0 was used for the subsequent imaging." (2.1 7m array)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan  
  > "Amplitude | Titan | Titan | Titan | Titan" (Table 1)
- flux scale uncertainty: _not stated_
- self calibration: Several phase self-cal steps; continuum noise improved by 2.7  
  > "Several phase self-calibration steps improved the noise level of the continuum image by a factor of 2.7" (2.1 7m array)

### Imaging

- task: tclean on continuum-subtracted ms; TP with sdimaging  
  > "The CASA tool `tclean` was used to generate data cubes from the continuum subtracted measurement set." (2.1 7m array)
- deconvolver: multiscale, scales 0 and 3  
  > "the `multiscale` deconvolver ((cite: Cornwell2008-no), with scales set to 0 and 3)" (2.1 7m array)
- weighting robust: Briggs robust = 1  
  > "we used a Briggs weighting with a robust parameter of 1" (2.1 7m array)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: auto-multithresh, noisethreshold=4.5, sidelobethreshold=1.25, clean to 0.3 sigma  
  > "we applied the *auto-multithresh* masking algorithm with the *noisethreshold*$=4.5$, and *sidelobethreshold*$=1.25$, to clean until a threshold of $0.3\sigma$ is reached" (2.1 7m array)
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub (7m); imcontsub (TP)  
  > "Continuum subtraction was performed with the CASA tool `uvcontsub` using the emission in the line-free regions." (2.1 7m array)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: TP regridded, divided by 7m PB, feather, then PB-corrected  
  > "After combining the image cubes with the CASA task `feather` we corrected the resulting image cube for the 7m PB." (2.2 Total Power array)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- CO(2-1)/CO(1-0) flux ratio 3.2  
  > "As in (cite: David2014-jn) we assume a CO(2-1) to CO(1-0) flux density ratio of $\num{3.2}$." (3.2) [from (cite: David2014-jn)]
- CLUMPFIND threshold 5 sigma and stepsize 3 sigma  
  > "Following (cite: Pineda2009-ir), we adopt the optimal threshold and stepsize parameters for `CLUMPFIND`, $5\sigma$ and $3\sigma$, respectively" (3.4) [from (cite: Pineda2009-ir)]
- Tex=42 K from Hydra A for column density  
  > "we assume $\SI{42}{K}$, as derived by (cite: Rose2019-tu) for Hydra A" (3.6) [from (cite: Rose2019-tu)]
- Cycle 0 observation details  
  > "Details about the ALMA cycle 0 observation can be found in (cite: David2014-jn)." (2) [from (cite: David2014-jn)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges for uvcontsub and imcontsub
- Image cell size and image size
- Self-calibration solution intervals
- Aperture centre coordinates
- Details of the masked-moment method and Gaussian fitting settings
- Which data selections for the uv-filtered mass vs scale test

## Analysis recipe

1. **Image 7m and TP cubes and combine**: tclean multiscale on 7m; sdimaging on TP; feather combination  
  > "Imaging was achieved through the CASA task `sdimaging` with a spheroidal gridding function and $\SI{10}{km\,s^{-1}}$ channel width." (2.2 Total Power array)
   - software: CASA
   - parameter: 10 km/s channels, robust 1  
  > "we used a Briggs weighting with a robust parameter of 1" (2.1 7m array)
   - fitting: _not stated_
   - validation: 7m spectrum compared with IRAM 30m within 6 arcsec  
  > "This comparison shows that essentially all of the CO(2-1) emission is recovered in the 7m observation" (3)
2. **Fit spectrum and derive molecular masses**: Three-Gaussian fit within 15 arcsec; masses from Galactic X_CO via moment maps and masked moments  
  > "We computed the total molecular mass within a $\SI{15}{\ensuremath{''}}$ radius aperture (a physical radius of $\SI{2.3}{kpc}$) using three methods" (3.2)
   - parameter: moment maps over -550 to 300 km/s; S/N>=5 for moment 1,2  
  > "by integrating the CO(2-1) emission between $\num{-550}$ and $\SI{300}{km\,s^{-1}}$" (3.1)
   - assumption: X_CO = 2e20 cm^-2 (K km/s)^-1; CO(2-1)/(1-0)=3.2; D_L=31.2 Mpc  
  > "X_\mathrm{CO} = \SI{2e20}{cm^{-2}\,(K\,km\,s^{-1})^{-1}}" (3.2)
   - fitting: Likelihood-ratio test of 2 vs 3 Gaussians  
  > "We use a likelihood-ratio analysis to verify the significance of this third component at high (negative) velocity." (3)
   - validation: Three mass methods agree  
  > "which are in relatively good agreement" (3.2)
3. **Detect molecular clouds**: CLUMPFIND on 7m cube with 10 km/s binning; inverted cube for false detection test  
  > "To know how many false detections are expected in our sample of clouds, we inverted the image cube (by multiplying with $-1$)" (3.4)
   - software: CLUMPFIND
   - parameter: 5 sigma threshold, 3 sigma step  
  > "$5\sigma$ and $3\sigma$, respectively, which results in 8 detected clouds" (3.4)
   - fitting: _not stated_
   - validation: Tested binnings 2-50 km/s; no false detections  
  > "We do not find any false detection." (3.4)
4. **Cloud sizes and virial parameter**: imfit on cloud moment maps, alpha=5R sigma^2/(GM)  
  > "We applied the CASA task `imfit` to the moment maps of the individual clouds to measure the extent (beam deconvolved)" (4.3.1)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
5. **Characterize AGN absorption lines**: Image 12m extended data with robust -2, baselines >1000 klambda; Gaussian fits; column density and virial mass  
  > "we imaged the 12m cycle 4 extended array observation using a Briggs robust parameter of -2, selecting only baselines longer than $\SI{1000}{k\lambda}$" (3.6)
   - software: CASA
   - assumption: Tex = 42 K, surface filling factor 1  
  > "This assumes a surface filling factor of 1" (3.6)
   - fitting: _not stated_
   - validation: Compared with perchanweightdensity imaging  
  > "Setting this parameter to `True` increases the amplitude of this line" (3.6)

## Software

- **CASA** 4.7.2 (calibration); 5.4.0 (imaging): calibration, imaging, continuum subtraction, feather, imfit  
  > "The 7m data were calibrated with CASA version 4.7.2 ((cite: McMullin2007-ed)) using the ALMA pipeline scripts, but CASA version 5.4.0 was used for the subsequent imaging." (2.1 7m array)
- **CLUMPFIND** : cloud identification  
  > "we used the `CLUMPFIND` algorithm ((cite: Williams1994-uc))" (3.4)
- **ZAP** : MUSE data reduction  
  > "The MUSE data were reduced using the v2.6.2 ESO MUSE pipeline within the Zurich Atmosphere Purge (ZAP) software" (4.1.2)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total molecular mass within 15 arcsec (three Gaussians) | 10.3e7 | 0.2e7 | Msun | 2 | $\SI{10.3(2)e7}{M_\odot}$, $\SI{9.5(12)e7}{M_\odot}$, and $\SI{10.0(1)e7}{M_\odot}$ |
| Molecular mass within 6 arcsec | 4.2e7 | 0.1e7 | Msun | 2 | obtained a (projected) mass of $\SI{4.2(1)e7}{M_\odot}$ |
| Number of CLUMPFIND clouds | 8 | not stated | dimensionless | 3 | which results in 8 detected clouds |
| Mean virial parameter | 8.6 | 3.4 | dimensionless | 4 | $\alpha = \num{8.6(34)}$ |
| Absorption line velocities | 255.5 and 264.7 | 0.3, 0.4 | km/s | 5 | $\num{255.5(3)}$ / $\num{6.6(3)}$ |
| H2 column density of absorbers | 1.5e20 | not stated | cm^-2 | 5 | N_{\mathrm{H_2}} = \SI{1.5e20}{cm^{-2}} |

## Qualitative findings

- Most flux is blueshifted and extended on kpc scales, suggesting low filling factor dispersed clouds  
  > "Most of the recovered flux is blueshifted with respect to the galaxy rest frame and is extended on kpc-scales" (abstract)

## Claim tuples

- H: The ACA 7m array recovers the single-dish flux missed by ALMA cycle 0 | E: Compare 7m, cycle 0 and IRAM 30m spectra in 6 arcsec aperture | R: Essentially all CO(2-1) emission recovered by 7m | F: Bulk of gas is diffuse on scales above 1 kpc | **supported**
- H: Absorbing clouds lie close to the AGN | E: 12m extended-array absorption spectra plus infall and cloud lifetime timescales | R: Projected distance within 5 pc; likely within 22 pc | F: Clouds likely within black hole sphere of influence | **partially**

## Reasoning

- Why this data: ACA short baselines needed to capture flux resolved out by ALMA 12m  
  > "This discrepancy motivated the additional observation of NGC 5044 with ACA to cover short baselines." (Summary)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Spatial variability of absorption not confirmed; X_CO may overestimate mass  
  > "Without deeper, high resolution data, unfortunately, we are unable to confirm the existence of a spatially variable absorption feature." (3.6)
- Caveat (inferred, ours): Summary text quotes 6.5e7 Msun and 10 clouds, inconsistent with 10.3e7 and 8 clouds in body
- Caveat (inferred, ours): Galactic X_CO may overestimate mass
- Caveat (inferred, ours): Absorber distances rest on scaling relations and assumed Tex

## Reproducibility

- Data public (paper): Project codes listed in acknowledgments  
  > "This paper makes use of the following ALMA data: 2011.0.00735.S, 2016.1.00533.S, 2016.2.00134.S, 2017.1.00784.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Line-free channels
- Missing: Cell/image sizes
- Missing: Self-cal solints
- Missing: Exact fitting setups
- Data volume (inferred): ~100-300 GB raw for four projects
- Score (inferred): 3/5, Imaging parameters mostly given, but several details missing and some internal inconsistencies.
- Rediscovery candidate: yes, Public data, fairly complete imaging recipe, numeric masses and cloud properties.

## Links

- Method: (cite: Williams1994-uc) (CLUMPFIND algorithm)
- Method: (cite: Pineda2009-ir) (CLUMPFIND parameter choice)
- Companion: (cite: David2014-jn) (Cycle 0 ALMA observation of NGC 5044)
- Companion: (cite: Temi2018-rr) (Independent analysis of cycle 0 data)

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
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 76,
  "stated": 49,
  "rate": 0.645
 },
 "evidence_ok": true
}
```
