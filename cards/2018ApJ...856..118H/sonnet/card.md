# Molecular Gas Reservoirs in Cluster Galaxies at z = 1.46

`2018ApJ...856..118H` | The Astrophysical Journal 2018 | first author: Hayashi, Masao | arXiv: 1803.00298 | DOI: 10.3847/1538-4357/aab3e7

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, high_z_galaxies, galaxy_clusters_and_sz
- Question: How large are molecular gas reservoirs, gas fractions and depletion times of galaxies in the z=1.46 cluster XMMXCS J2215.9-1738 compared with field scaling relations, and how much gas remains in quiescent core galaxies?  
  > "We use the ALMA data to investigate molecular gas reservoirs in the member galaxies and then discuss the evolution of their star formation activities in terms of star formation efficiency and gas consumption." (1 Introduction)
- Target **XMMXCS J2215.9-1738 cluster**: coordinates not stated (Band 7 sources near 22 15 58, -17 37 50)  
  > "XMMXCS J2215.9-1738 galaxy cluster at $z=1.457$ (cite: Stanford2006)" (1 Introduction); "the radius of the galaxy cluster is $R_{200}$ = 0.8 Mpc (cite: Hilton2010)" (1 Introduction); z/distance z=1.457; R200 = 0.8 Mpc; H0=70, Om=0.3, OL=0.7  
  > "XMMXCS J2215.9-1738 galaxy cluster at $z=1.457$ (cite: Stanford2006)" (1 Introduction); "the radius of the galaxy cluster is $R_{200}$ = 0.8 Mpc (cite: Hilton2010)" (1 Introduction); distance from Stanford2006 (redshift); Hilton2010 (R200)  
  > "XMMXCS J2215.9-1738 galaxy cluster at $z=1.457$ (cite: Stanford2006)" (1 Introduction); "the radius of the galaxy cluster is $R_{200}$ = 0.8 Mpc (cite: Hilton2010)" (1 Introduction)

## Data provenance

- ALMA projects: 2015.1.00779.S, 2012.1.00623.S
- bands: Band 3 and Band 7  
  > "our ALMA observations in Band 3 and Band 7" (1 Introduction)
- frequencies and spectral setup: Band 3: 93.03–94.86 GHz, 13.906 MHz channels (~12.5 km/s); Band 7: four SPWs at 338, 340, 350, 352 GHz, 1.875 GHz each  
  > "The spectral coverage is 93.03 – 94.86 GHz with a spectral resolution of 13.906 MHz ($\sim$ 12.5 km s$^{-1}$)." (2.1 ALMA Band 3); "Four spectral windows are set at central frequencies of 338, 340, 350 and 352 GHz with each bandwidth of 1.875 GHz, respectively." (2.2 ALMA Band 7)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Band 3: 1.79" x 1.41"; Band 7: 0.181" x 0.157" (PA 44.7 deg)  
  > "The synthesized beam size is 1.79$''$ $\times$ 1.41$''$." (2.1 ALMA Band 3); "The synthesized beam size is 0.181$''$ $\times$ 0.157$''$ with a position angle of 44.7 degrees." (2.2 ALMA Band 7)
- max recoverable scale: _not stated_
- sensitivity: Band 3: 0.12 mJy/beam at 400 km/s; Band 7: 0.061–0.068 mJy/beam  
  > "Typical noise level of the mosaicked 3D cubes is 0.12 mJy beam$^{-1}$ at velocity resolutions of 400 km s$^{-1}$." (2.1 ALMA Band 3); "Typical noise levels of these images are 0.061 – 0.068 mJy beam$^{-1}$" (2.2 ALMA Band 7)
- time on source: Band 3: 1.04 h per pointing (3 pointings); Band 7: 7.06 min per pointing (10 pointings)  
  > "Integration time is 1.04 hours per each pointing." (2.1 ALMA Band 3); "Integration time is 7.06 minutes per each pointing." (2.2 ALMA Band 7)
- observing dates: Band 7: 2015 July  
  > "The observations in Band 7 were conducted in 2015 July." (2.2 ALMA Band 7)
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (230.538 GHz)
- Other facility **Subaru/Suprime-Cam**: optical imaging B, Rc, i', z', NB912, NB921  
  > "We have optical images taken with Subaru/Suprime-Cam in $B, R_c, i', z'$, NB912 and NB921" (2.3 Archival imaging data)
- Other facility **CFHT MegaCam/WIRCam**: u*, g' and J, H, Ks images  
  > "NIR images taken with CFHT/WIRCam in $J, H$ and $K_s$" (2.3 Archival imaging data)
- Other facility **HST WFC3**: F125W, F140W, F160W images  
  > "Wide Field Camera 3 (WFC3) on HST in F125W, F140W, and F160W filters" (2.3 Archival imaging data)
- Other facility **Spitzer IRAC/MIPS**: 3.6–5.8 um and 24 um data  
  > "MIR data of Spitzer/IRAC 3.6–5.8 $\mu$m and MIPS 24 $\mu$m" (2.3 Archival imaging data)
- External data: CO(2-1) luminosities and line detections of 17 galaxies from Band 3  
  > "The CO(2–1) luminosities are derived in (cite: Hayashi2017) from the intensity map integrated in velocity by the width of emission line (2$\times$FWHM)." (3.1 molecular gas mass) [from (cite: Hayashi2017)]
- External data: Field scaling relations of gas fraction and depletion time  
  > "Scaling relations of gas to stellar mass ratio ($\rm M_{gas}/M_{stellar}$) and depletion time scale on both specific SFR and its offset from the MS are derived by (cite: Tacconi2018)" (4.1 Comparison with the scaling relations) [from (cite: Tacconi2018)]
- External data: Main sequence at z=1.46  
  > "We assume the MS of star-forming galaxies at $z=1.46$ given by (cite: Speagle2014)" (3.2 Gas mass fraction and depletion time scale) [from (cite: Speagle2014)]
- External data: Gas, stellar mass and SFR data of z~1.6 clusters for comparison  
  > "using the information available from the literature (cite: Noble2017; Rudnick2017) for proper comparison with our results" (4.2 Comparison with other clusters) [from (cite: Noble2017; Rudnick2017)]

## Processing

### Calibration

- pipeline or manual: CASA with standard ALMA pipeline  
  > "Calibration of the raw data is conducted using the Common Astronomy Software Applications (cite: McMullin2007) with a standard ALMA pipeline." (2.2 ALMA Band 7)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs robust = 2.0 (natural weighting)  
  > "The Briggs weighting with the robust parameter of 2.0 (i.e., natural weighting)" (2.2 ALMA Band 7)
- uv taper: taper to 0.48" x 0.46" beam for flux check  
  > "We also measure the flux densities in the uv-tapered map with the synthesized beam size of 0.48$''$ $\times$ 0.46$''$" (2.2 ALMA Band 7)
- cell size: _not stated_
- image size: _not stated_
- masking: CLEAN threshold 0.35 mJy (~5 sigma)  
  > "a CLEAN threshold of 0.35 mJy ($\sim5\sigma$) are adopted to make CLEANed images" (2.2 ALMA Band 7)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: five nearest Band 7 pointings mosaicked  
  > "Among ten pointings, the data at five pointings nearest from the cluster center are mosaiced to make a single image" (2.2 ALMA Band 7)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Band 3 data details, line search and CO luminosities  
  > "Since the details of the Band 3 data and source detection in the data are described in the paper, we briefly mention them in this section." (2.1 ALMA Band 3) [from (cite: Hayashi2017)]
- CO-to-H2 conversion factor and metallicity dependence  
  > "The conversion factor from the CO luminosity to the molecular gas mass given by (cite: Tacconi2018) is adopted to estimate the molecular gas mass." (3.1 molecular gas mass) [from (cite: Tacconi2018)]
- MIPS PSF-fitted photometry  
  > "We conduct PSF-fitted photometry with `IRAF/DAOPHOT` in the MIPS data, according to the previous studies (cite: Magnelli2009)." (2.5.1 multi-band photometry) [from (cite: Magnelli2009)]

### Not stated but needed to reproduce (our reading)

- Which ALMA execution blocks, CASA version and pipeline version were used
- Band 7 cell size, image size, and mask details
- Flux calibrator and flux scale uncertainty
- Stacking procedure details (weights, rest-frame shift, velocity width)
- Exact Scoville2016 equation parameters and gas-to-dust ratio function
- SED-fit fastpp configuration beyond the grid ranges
- Tapered-map photometry choice per source relies on the 1 sigma criterion; detection algorithm for sources not specified

## Analysis recipe

1. **Band 7 imaging and source detection**: Natural-weighted CLEAN images; search for pixels >4.6 sigma; check with inverted data  
  > "We search for sources with a pixel count larger than $4.6\sigma$ in each image." (2.2 ALMA Band 7)
   - software: CASA
   - parameter: robust 2.0, CLEAN threshold 0.35 mJy  
  > "The Briggs weighting with the robust parameter of 2.0 (i.e., natural weighting) and a CLEAN threshold of 0.35 mJy ($\sim5\sigma$)" (2.2 ALMA Band 7)
   - fitting: _not stated_
   - validation: Only one negative detection with inverted data; sources without counterparts appear below the threshold  
  > "we also apply the same threshold to the inverted data to select pixels with a large negative value and then find only one negative detection." (2.2 ALMA Band 7)
2. **Band 7 aperture photometry**: 0.44" diameter aperture; errors from 10,000 random apertures; use tapered map (1.0" aperture) if inconsistent  
  > "The error of the flux densities are estimated from the 10,000 measurements with the same aperture at the random positions over the individual images." (2.2 ALMA Band 7)
   - fitting: Gaussian fit to histogram of random measurements  
  > "The 1$\sigma$ error is derived by fitting a Gaussian to the histogram of the random measurements." (2.2 ALMA Band 7)
   - validation: Compared with uv-tapered map for resolved-out flux  
  > "We also measure the flux densities in the uv-tapered map with the synthesized beam size of 0.48$''$ $\times$ 0.46$''$ to verify whether there is a flux of an extended component resolved out." (Data, ALMA Band 7)
3. **Band 3 CO line search**: Clumpfind on cubes at 50-600 km/s resolutions, SNR>5, cross-match with optical-NIR  
  > "The emission-line search is performed in the cubes with different velocity resolutions of 50, 100, 200, 400, and 600 km s$^{-1}$." (2.1 ALMA Band 3)
   - software: Clumpfind
   - fitting: _not stated_
   - validation: 21 candidates, 17 with counterparts accepted  
  > "we conclude that 17 emission lines with counterparts in the optical–NIR data are secure detections." (2.1 ALMA Band 3)
4. **Stellar mass, SFR, and UVJ colours**: SED fitting with redshift fixed; SFR from UV+24um where detected  
  > "We use the C++ version of `FAST` code (cite: Kriek2009) to perform the spectral energy distribution (SED) fitting." (2.5.2 stellar mass, SFR, and rest-frame colors)
   - software: FAST, SExtractor, IRAF/DAOPHOT, MOPEX
   - parameter: log tau 8.5-10.0, age 0.1-10 Gyr, AV 0-3, solar metallicity  
  > "The ages of 0.1–10.0 Gyr are acceptable with a step of $\Delta\log(\rm age/yr)=$ 0.1." (2.5.2 stellar mass, SFR, and rest-frame colors)
   - assumption: BC03 templates, exponentially declining SFH, Calzetti extinction, Chabrier IMF  
  > "The extinction curve of (cite: Calzetti2000) is assumed and $A_V$ ranges from 0.0 to 3.0." (2.5.2 stellar mass, SFR, and rest-frame colors)
   - fitting: Monte Carlo 100 times per galaxy for 1 sigma errors  
  > "Monte Carlo simulation is performed 100 times for each galaxy to estimate a $1\sigma$ error in stellar mass and SFR." (2.5.2 stellar mass, SFR, and rest-frame colors)
   - validation: _not stated_
5. **Derive molecular gas masses**: CO luminosity with Tacconi2018 alpha_CO; dust continuum with Scoville2016 eq. 16  
  > "We also use the equation (16) of (cite: Scoville2016) to estimate molecular gas mass from dust continuum emission at 870 $\mu$m" (3.1 molecular gas mass)
   - parameter: L'CO(1-0)/L'CO(2-1)=1.2, alpha_CO(1-0)=4.36 (4.99–7.31 after metallicity correction)  
  > "We use $L'_{\rm CO(1-0)}/L'_{\rm CO(2-1)}=1.2$ and $\alpha_{\rm CO(1-0)}=4.36$." (3.1 molecular gas mass)
   - assumption: Td = 25 K; stellar-mass-dependent gas-to-dust ratio per Tacconi2018  
  > "the dust temperature of $T_d=25$ K is assumed" (3.1 molecular gas mass)
   - fitting: _not stated_
   - validation: CO and dust gas masses consistent  
  > "The molecular gas masses estimated from the two ways are consistent." (3.1 molecular gas mass)
6. **Gas fraction, depletion time and comparison with scaling relations**: f_gas = Mgas/(Mgas+Mstar), tau = Mgas/SFR; compare with Tacconi2018 relations with Speagle2014 MS  
  > "$f_{\rm gas}=M_{\rm gas}/(M_{\rm gas}+M_{\rm stellar})$, and depletion time scale, $\tau=M_{\rm gas}$/SFR" (3.2 Gas mass fraction and depletion time scale)
   - fitting: _not stated_
   - validation: Compared with z~1.6 clusters  
  > "The comparison with the results in the galaxy clusters at $z\sim1.6$ show that our results are consistent with the other clusters at similar redshifts" (Discussion, Comparison with other clusters at similar redshifts)
7. **Stack Band 3 spectra of quiescent and star-forming galaxies**: Stack spectroscopically confirmed members within 0.5 R200 shifted to rest frame; 5 sigma upper limits from 400 km/s intensity map  
  > "Using the intensity map integrated in velocity by 400 km s$^{-1}$, the average CO(2–1) line flux and the 5$\sigma$ upper limit flux are estimated" (4.3 Molecular gas reservoirs of quiescent galaxies)
   - fitting: _not stated_
   - validation: Procedure checked by stacking individually detected galaxies  
  > "we make sure the validity of our procedure by stacking the data for the member galaxies with CO(2–1) detected individually." (4.3 Molecular gas reservoirs of quiescent galaxies)

## Software

- **CASA** : calibration and imaging of Band 7 data  
  > "Calibration of the raw data is conducted using the Common Astronomy Software Applications (cite: McMullin2007) with a standard ALMA pipeline." (2.2 ALMA Band 7)
- **Clumpfind** : emission-line search in Band 3 cubes  
  > "We use `Clumpfind` (cite: Williams1994) to search for emission lines on the data cube." (2.1 ALMA Band 3)
- **SExtractor** : optical, NIR and IRAC photometry  
  > "`SExtractor` (cite: Bertin1996) is used for photometry in the optical, NIR and IRAC data." (2.5.1 multi-band photometry)
- **FAST (C++ version)** : SED fitting  
  > "We use the C++ version[^1] of `FAST` code (cite: Kriek2009)" (2.5.2 stellar mass, SFR, and rest-frame colors)
- **MOPEX** : coadd MIPS 24um images  
  > "coadd them with `MOPEX` (MOsaicker and Point source EXtractor)" (2.3 Archival imaging data)
- **IRAF/DAOPHOT** : PSF-fitted MIPS photometry  
  > "We conduct PSF-fitted photometry with `IRAF/DAOPHOT` in the MIPS data" (2.5.1 multi-band photometry)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Band 7 870um detections | 9 | not stated | sources | 1 | We have detected 9 sources at 870$\mu$m from the Band 7 data |
| Band 7 flux density ALMA.B7.01 | 2.58 | 0.23 | mJy | 2 | 2.58 $\pm$ 0.23$^{c}$ |
| CO(2-1) luminosity range | (4.5–22)e9 | not stated | K km/s pc^2 | 0 | ranges (4.5–22) $\times10^{9}$ K km $^{-1}$ pc$^2$ |
| Average gas fraction within 0.5 R200 | 0.29–0.53 | range from limits | dimensionless | 6 | $\langle f_{gas} \rangle=$0.29–0.53 and $\langle \tau \rangle=$0.83–2.3 Gyr |
| Average depletion time within 0.5 R200 | 0.83–2.3 | range from limits | Gyr | 6 | $\langle f_{gas} \rangle=$0.29–0.53 and $\langle \tau \rangle=$0.83–2.3 Gyr |
| Quiescent stack gas mass upper limit | <0.93e10 | 5 sigma limit | Msun | 7 | $<$0.93 |
| Quiescent stack gas fraction upper limit | <0.08 | 5 sigma limit | dimensionless | 7 | the gas fraction of $<$ 0.08 and the depletion time scale of $<$ 9.8 Gyr |
| Quiescent stack depletion time upper limit | <9.8 | 5 sigma limit | Gyr | 7 | the gas fraction of $<$ 0.08 and the depletion time scale of $<$ 9.8 Gyr |

## Qualitative findings

- Cluster galaxies have larger gas fractions and depletion times than field scaling relations  
  > "The member galaxies with CO and/or dust continuum detected in the cluster tend to have larger gas fraction and larger depletion time, compared with those from the scaling relations." (4.1 Comparison with the scaling relations)

## Claim tuples

- H: Do cluster galaxies at z=1.46 have gas reservoirs different from field galaxies? | E: Compare gas fraction and depletion time of 18 detected members with Tacconi2018 scaling relations | R: Larger gas fraction and depletion time than expected | F: Cluster environment feeds gas but reduces star formation efficiency | **supported**
- H: Is the gas in massive quiescent core galaxies exhausted? | E: Stack Band 3 spectra of 12 quiescent galaxies within 0.5 R200 | R: No CO detection; gas fraction <~10% | F: Massive core galaxies quench while consuming most gas | **supported**
- H: Do deviations depend on cluster-centric position or accretion phase? | E: Compare ratios to scaling relations vs radius and phase space | R: Galaxies closer to the centre show larger deviation, though statistics are poor | F: Environmental effects acting as galaxies fall in | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Same alpha_CO as Tacconi2018 to enable fair comparison with scaling relation  
  > "The conversion factors that we apply in this work are the same as in (cite: Tacconi2018), which enables a fair comparison of our results with the scaling relation." (3.1 molecular gas mass)
- Alternative: alpha_CO=1 (Stach2017) considered but rejected as CO and dust masses agree  
  > "However, we find that the gas masses we estimate by the different ways, i.e, CO and dust continuum, are consistent with each other even for the two galaxies" (3.1 molecular gas mass)
- How they decided it was enough: _not stated_
- Limitation (authors): Gas mass may be overestimated by ~1.5 if cluster galaxies are more metal-rich  
  > "This can result in the overestimation of molecular mass by a factor of $\sim1.5$" (4.1 Comparison with the scaling relations)
- Limitation (authors): Patchy Band 7 coverage so number density is a lower limit  
  > "the number density would be a lower limit" (2.2 ALMA Band 7)
- Caveat (inferred, ours): Gas masses depend strongly on assumed alpha_CO and CO excitation ratio
- Caveat (inferred, ours): Small sample; no uncertainty on key scaling-relation ratios
- Caveat (inferred, ours): Dust masses rely on fixed Td=25 K
- Caveat (inferred, ours): Stacking upper limits rely on spectroscopic redshifts of a biased sample

## Reproducibility

- Data public (paper): ALMA programs listed; public availability not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.1.00623.S and ADS/JAO.ALMA#2015.1.00779.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters (cell, size, masks)
- Missing: Stacking details
- Missing: Table values of ratios to scaling relations
- Missing: Exact CASA/pipeline versions
- Data volume (inferred): ~50-100 GB raw for two small programs
- Score (inferred): 3/5, Data identifiable and many steps described, but imaging, stacking and versions are vague and much depends on prior papers.
- Rediscovery candidate: no, Recipe depends on inherited Band 3 results and external scaling relations; settings incomplete.

## Links

- Method: (cite: Tacconi2018) (alpha_CO, gas-to-dust ratio and scaling relations)
- Method: (cite: Scoville2016) (dust continuum gas mass equation)
- Method: (cite: Hayashi2017) (Band 3 data and CO detections)
- Companion: (cite: Hayashi2017) (initial Band 3 CO(2-1) results in the same cluster)
- Companion: (cite: Stach2017) (independent ALMA Band 6 study of the same cluster)
- Related: PHIBSS
- Related: CFHTLS-Deep
- Related: WIRCam Deep Survey

## Checks

```json
{
 "quotes": 80,
 "quotes_ok": 80,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2011.1.00623.S"
 ],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 90,
  "stated": 58,
  "rate": 0.644
 },
 "evidence_ok": true
}
```
