# ALMA observations of transient heating in a solar active region

`2020A&A...643A..41D` | Astronomy and Astrophysics 2020 | first author: da Silva Santos, J. M. | arXiv: 2006.14564 | DOI: 10.1051/0004-6361/202038755

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: sun
- Question: Are Ellerman bombs, UV bursts and flaring active-region fibrils visible in the ALMA 3 mm continuum, and what temperatures and formation heights do they have?  
  > "We aim to investigate the temperature enhancements and formation heights of solar active-region brightenings such as Ellerman bombs (EBs), ultraviolet bursts (UVBs), and flaring active-region fibrils (FAFs)" (abstract)
- Target **Active region NOAA 12738 (pores near sunspot periphery)**: coordinates _not stated_; z/distance near disk center, mu=0.98  
  > "On 13 April 2019, ALMA was pointed at a group of pores in the periphery of a large sunspot in NOAA 12738 near the disk center ($\mu=0.98$" (2.1 Data reduction and calibration); distance from _not stated_

## Data provenance

- ALMA projects: 2018.1.01518.S
- bands: Band 3 (3 mm, 100 GHz)  
  > "The ALMA Band 3 data were acquired in two execution blocks, each consisting of three 10-minute scans separated by 140-second calibration intervals." (2.1 Data reduction and calibration)
- frequencies and spectral setup: four sidebands (94, 96, 104, 106 GHz)  
  > "The four sidebands (94, 96, 104, 106 GHz) were included together in the mapping in order to improve instantaneous $u,v$ coverage." (2.1 Data reduction and calibration)
- continuum bandwidth: _not stated_
- arrays: 50 antennas (41 x 12m and 9 x 7m); 42 used most of the time  
  > "The array contained 50 antennas (41 $\times$ 12m and 9 $\times$ 7m), of which eight (6 $\times$ 12m, 2 $\times$ 7m) were flagged throughout" (2.1 Data reduction and calibration)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.2 arcsec  
  > "We note that the maximum spatial resolution of these ALMA observations is $\sim$1.2$''$ and thus similar to AIA." (2.1 Data reduction and calibration)
- max recoverable scale: _not stated_
- sensitivity: noise 20 K in difference map of consecutive maps  
  > "The typical noise level in the difference map made from consecutive maps is 20 K." (2.1 Data reduction and calibration)
- time on source: _not stated_
- observing dates: 13 April 2019, 18:19:52-18:54:55 and 19:15:32-19:50:31  
  > "The two periods covered by the execution blocks were 18:19:52-18:54:55 and 19:15:32-19:50:31." (2.1 Data reduction and calibration)
- pi or archival as stated: _not stated_
- Other facility **SDO/AIA**: UV and EUV images used to identify EBs and nanoflares, DEM analysis  
  > "We also use ultraviolet (UV) images taken with the Atmospheric Imaging Assembly (cite: 2012SoPh..275...17L)" (2.1 Data reduction and calibration)
- Other facility **SDO/HMI**: photospheric magnetograms  
  > "photospheric magnetograms obtained with the Helioseismic and Magnetic Imager (cite: 2012SoPh..275..207S)" (2.1 Data reduction and calibration)
- Other facility **ALMA single-dish**: calibrated single-dish image used for absolute temperature scale  
  > "we compared the average temperature within the 60$''$ region of interest in the interferometer maps with the corresponding temperature at that location in a calibrated single-dish image" (2.1 Data reduction and calibration)
- External data: 3D Bifrost flux emergence simulation snapshot  
  > "we used one snapshot of a 3D r-MHD flux emergence simulation performed with the `Bifrost` code (cite: 2011A&A...531A.154G) and analyzed by (cite: 2017ApJ...839...22H)" (4 Synthetic millimeter continuum) [from (cite: 2017ApJ...839...22H)]
- Simulation/model as data: Bifrost snapshot, 504x504x496 px, 48 km horizontal; 3 mm continuum synthesized with STIC in NLTE  
  > "The box size is 504$\times$504$\times$496 px and the resolution is 48 km per px in the horizontal direction" (4 Synthetic millimeter continuum)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: absolute scale set by adding 7700 K from single-dish comparison  
  > "This resulted in the addition of 7700 K to the interferometer maps." (2.1 Data reduction and calibration)
- self calibration: phase self-calibration with progressively smaller intervals  
  > "The data in each execution block were mapped and self-calibrated in phase with progressively smaller intervals to remove atmospheric effects." (2.1 Data reduction and calibration)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: 0.3 arcsec  
  > "We made 512$\times$512 pixel maps with a cell size of 0.3$''$" (2.1 Data reduction and calibration)
- image size: 512x512 pixels; analysis within inner 60 arcsec  
  > "but quantitative analysis is restricted to the inner 60$''$ regions of the images" (2.1 Data reduction and calibration)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: applied  
  > "The final maps used here were primary-beam-corrected and restored with a Gaussian beam 1.2$''$ in width." (2.1 Data reduction and calibration)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: Gaussian 1.2 arcsec  
  > "restored with a Gaussian beam 1.2$''$ in width" (2.1 Data reduction and calibration)
- final rms: _not stated_

### Inherited from earlier work

- Simulation setup details  
  > "to which we refer for a detailed description of the setup" (4 Synthetic millimeter continuum) [from (cite: 2017ApJ...839...22H)]
- DEM inversion code  
  > "using the regularized DEM inversion code[^4] described in (cite: 2012A&A...539A.146H)" (3.4 Differential emission measure analysis) [from (cite: 2012A&A...539A.146H)]
- Coronal contribution approach  
  > "Following the approach of (cite: 2013PASJ...65S...8A) and (cite: 2017ApJ...845L..19B)" (3.4 Differential emission measure analysis) [from (cite: 2013PASJ...65S...8A); (cite: 2017ApJ...845L..19B)]

### Not stated but needed to reproduce (our reading)

- ALMA reduction software (CASA?) and version, and imaging task/parameters (weighting, deconvolver)
- self-calibration solution intervals
- how the calibrated single-dish image was obtained
- exact co-alignment offsets and angle between ALMA and SDO
- EBDETECT parameters beyond threshold, and 1700 A reference level
- absolute coordinates of the pointing
- time cadence of ALMA maps and how they were made

## Analysis recipe

1. **Image ALMA Band 3 and set absolute temperature scale**: Phase self-calibrated mapping of all four sidebands, primary beam correction, conversion to Tb, offset by single-dish comparison  
  > "The maps are converted from flux to brightness temperature." (2.1 Data reduction and calibration)
   - parameter: cell 0.3 arcsec, beam 1.2 arcsec, +7700 K  
  > "This resulted in the addition of 7700 K to the interferometer maps." (2.1 Data reduction and calibration)
   - fitting: _not stated_
   - validation: _not stated_
2. **Prepare and co-align SDO data**: AIA respiking, SunPy alignment, HMI deconvolution with Enhance, degradation and stray-light correction, rebin to 0.3 arcsec; refine alignment with 304 A structures  
  > "the co-alignment was refined by taking advantage of the good correspondence between the mm and EUV bright structures" (2.1 Data reduction and calibration)
   - software: SolarSoftWare, SunPy, Enhance
   - fitting: _not stated_
   - validation: visual verification with other events  
  > "The accuracy was visually verified by the spatial coincidence of other events at different times." (2.1 Data reduction and calibration)
3. **Search for EBs and compare to Band 3**: EBDETECT on AIA 1700 A, 9 sigma events, measure Tb and light-curve correlations  
  > "Here, we only consider $9\sigma$ events" (3.1 Ellerman bombs as sub-canopy events)
   - software: EBDETECT
   - parameter: 9 sigma cores, 5 sigma halos  
  > "the EBs (both the $9\sigma$ cores and $5\sigma$ extended halos) are undetected in the ALMA Band 3 maps." (3.1 Ellerman bombs as sub-canopy events)
   - assumption: 1700 A continuum as EB proxy in absence of H-alpha  
  > "In the absence of H$\alpha$ observations, the 1700 Å continuum can be used as a proxy for EBs" (3.1 Ellerman bombs as sub-canopy events)
   - fitting: _not stated_
   - validation: _not stated_
4. **DEM and thermal energy of EUV kernels**: Regularized DEM inversion with six AIA filters; E_th ~ 3 n_e k T V  
  > "We estimated an order of magnitude for the thermal energy of the EUV kernels (Sect. [3.2](#section:DEM)) as $E_{\rm th}$$\sim$3$n_{\rm e}k_{\rm B}TV,$" (3.4 Differential emission measure analysis)
   - software: DEMREG, CHIANTI v9
   - parameter: 4x4 px averaged intensities; 20% systematic uncertainty  
  > "we include a systematic uncertainty factor of 20% to account for uncertainties in atomic data" (3.4 Differential emission measure analysis)
   - assumption: n_e ~1e9 cm^-3 or sqrt(EM/w) with filling factor 1; depth equals width  
  > "and a filling factor of one is assumed" (3.4 Differential emission measure analysis)
   - fitting: 2D Gaussian FWHM for kernel sizes  
  > "The dimensions are estimated by fitting a 2D Gaussian to the kernels" (3.4 Differential emission measure analysis)
   - validation: _not stated_
5. **Coronal contribution to 3 mm Tb**: Integrate free-free opacity times DEM over 5.5<=logT<=7.3 in Rayleigh-Jeans limit  
  > "We computed the DEM in each pixel of the FOV, and the integration was carried between 5.5$\leq\log T\leq$7.3" (3.4 Differential emission measure analysis)
   - assumption: fully ionized hydrogen plasma  
  > "assuming a fully ionized hydrogen plasma" (3.4 Differential emission measure analysis)
   - fitting: _not stated_
   - validation: _not stated_
6. **Synthetic 3 mm continuum from Bifrost**: NLTE computation with STIC (six-level hydrogen), AIA EUV synthesized with response functions; smear to 1.2 arcsec  
  > "computed in nonlocal thermodynamic equilibrium (NLTE) using the STockholm Inversion Code" (4 Synthetic millimeter continuum)
   - software: Bifrost, STIC
   - fitting: _not stated_
   - validation: compared with observed Tb at kernels  
  > "which agrees with the typical values that we observe at the bright kernels" (4 Synthetic millimeter continuum)
7. **Wavelet periodicity analysis**: Wavelet transform without detrending, 99% confidence assuming white noise  
  > "We find evidence for periodicities in the $\approx$50-150 s range in NF1 and NF3 at a 99% confidence level assuming white noise." (7 Millimeter brightness oscillations)
   - software: Python wavelet software (Torrence & Compo)
   - fitting: _not stated_
   - validation: 5x5 px averaging to test jitter  
  > "This has no significant effect on their power spectra." (7 Millimeter brightness oscillations)

## Software

- **EBDETECT** : EB detection in AIA 1700 A  
  > "We searched for EB signatures in AIA 1700 Å using the `EBDETECT`[^3] code" (3.1 Ellerman bombs as sub-canopy events)
- **SunPy** : alignment, scaling, derotation, resampling of AIA and HMI  
  > "The AIA and HMI data were further processed with routines provided in the `SunPy` package" (2.1 Data reduction and calibration)
- **aia_respike (SolarSoftWare)** : respiking AIA level-1 data  
  > "We therefore "respiked" the level-1 AIA data products using the IDL code `aia_respike` in SolarSoftWare" (2.1 Data reduction and calibration)
- **Enhance** : deconvolution and upsampling of HMI  
  > "deconvolved and upsampled to 0.3$''$ per pixel using the `Enhance` deep learning code" (2.1 Data reduction and calibration)
- **DEMREG** : DEM inversion  
  > "using the regularized DEM inversion code[^4] described in (cite: 2012A&A...539A.146H)" (3.4 Differential emission measure analysis)
- **CHIANTI** v9: AIA instrumental responses  
  > "We use time-dependent AIA instrumental responses obtained from SSW with CHIANTI v9" (3.4 Differential emission measure analysis)
- **Bifrost** : 3D r-MHD simulation  
  > "performed with the `Bifrost` code" (4 Synthetic millimeter continuum)
- **STIC** : NLTE synthesis of 3 mm continuum  
  > "using the STockholm Inversion Code[^5]" (4 Synthetic millimeter continuum)
- **MATLAB** 2018b: image processing  
  > "MATLAB and the Image Processing Toolbox release 2018b" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Max Tb in NF kernels | 14300 | not stated | K | 1 | The highest brightness temperature at 3 mm that we observe in the EUV kernels is $T_{\rm b}$$\approx$14 300 K. |
| Mean Tb of EBs in Band 3 | 7900 | ±300 | K | 3 | the mean and standard deviation of the brightness of the EBs in Band 3 are $T_{\rm b}$$\sim$7900$(\pm 300)\rm \,K$. |
| Number of EBs in ALMA FOV | 20 | not stated | count | 3 | We identified a total of 20 EBs within the ALMA FOV throughout the time span of the observations. |
| Thermal energy NF1 (n_e from EM) | 4e25 | ±1e25 | erg | 4 | $E_{\rm th}$$\approx$$4(\pm1)\times10^{25}$ erg (NF1) |
| Coronal contribution to Tb in NF1/NF2/NF3 | 3% / 4% / 7% | not stated | percent | 5 | We find a relative contribution of $\sim$3% in NF1, 4% in NF2, and 7% in NF3. |
| Plane-of-sky velocity of heat fronts | 37 and 340 | not stated | km/s | 0 | a plane-of-sky velocity of $\approx$$340\rm\,km\,s^{-1}$ |
| Wavelet periodicities | 50-150 | not stated | s | 7 | We find evidence for periodicities in the $\approx$50-150 s range in NF1 and NF3 |
| Correlation of simulated Tb(3mm) with gas T at tau=1 | 0.92 | not stated | dimensionless | 6 | are well-correlated ($r=0.92$) |

## Qualitative findings

- EBs have no 3 mm counterpart, consistent with sub-canopy formation  
  > "We report the null detection of EBs in the 3 mm continuum at $\sim$1.2$''$ spatial resolution" (abstract)

## Claim tuples

- H: EBs are detectable in ALMA Band 3 | E: EBDETECT on AIA 1700 A, compared with Band 3 maps and light curves | R: None of 20 EBs detected; weak correlations | F: EBs are sub-canopy and do not heat the upper chromosphere | **supported**
- H: Bursts and FAF-like events appear in Band 3 | E: Compared AIA EUV kernels with ALMA maps and time series | R: Tb up to ~14 kK, velocities 37-340 km/s | F: Multiple mm-bursts and FAF-like events exist | **supported**
- H: The corona contributes to the 3 mm brightness | E: DEM-based opacity integration | R: up to ~7% at NF sites | F: Non-negligible but partial contribution | **partially**
- H: ALMA can detect mm counterparts of UVBs and flares | E: Synthetic 3 mm from Bifrost | R: UVB and FAF-like features with high Tb; no H-alpha EB counterparts | F: Simulation confirms detectability | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Simulation magnetic topology not comparable to the observed region; no IRIS data; DEM coronal estimates are lower limits  
  > "Furthermore, the magnetic topology is not directly comparable to the observed active region" (4 Synthetic millimeter continuum)
- Caveat (inferred, ours): Single snapshot simulation compared to a long observed series
- Caveat (inferred, ours): Absolute Tb offset from single-dish adds systematic uncertainty
- Caveat (inferred, ours): Co-alignment of ALMA/SDO refined by eye on the features studied, risking circularity
- Caveat (inferred, ours): Nanoflare energies depend on assumed density and geometry

## Reproducibility

- Data public (paper): ALMA data identified by project code 2018.1.01518.S; movie online  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2018.1.01518.S" (Acknowledgements)
- Products in archive: _not stated_
- Missing: ALMA imaging scripts and solint
- Missing: Single-dish reference image
- Missing: Bifrost snapshot
- Missing: alignment parameters
- Data volume (inferred): Large time-series solar data, likely hundreds of GB for ALMA plus SDO cutouts
- Score (inferred): 3/5, Data are public and the DEM and EB steps are described, but solar ALMA imaging details, the simulation snapshot and alignment are missing.
- Rediscovery candidate: no, ALMA imaging recipe incomplete and requires specialized solar reduction and a simulation snapshot.

## Links

- Method: (cite: 2012A&A...539A.146H) (DEM inversion method)
- Method: (cite: 2019A&A...626A...4V) (EBDETECT)
- Method: (cite: 2018A&A...614A...5D) (Enhance deconvolution)
- Companion: (cite: 2017ApJ...839...22H) (Bifrost simulation used)
- Companion: (cite: 2017ApJ...841L...5S) (earlier ALMA plasmoid detection)

## Checks

```json
{
 "quotes": 65,
 "quotes_ok": 65,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 89,
  "stated": 51,
  "rate": 0.573
 },
 "evidence_ok": true
}
```
