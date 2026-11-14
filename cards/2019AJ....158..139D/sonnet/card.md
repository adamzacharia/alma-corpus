# First ALMA Millimeter-wavelength Maps of Jupiter, with a Multiwavelength Study of Convection

`2019AJ....158..139D` | The Astronomical Journal 2019 | first author: de Pater, Imke | arXiv: 1907.11820 | DOI: 10.3847/1538-3881/ab3643

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: solar_system
- Question: What do the first ALMA 1.3 and 3 mm maps of Jupiter, together with contemporaneous multiwavelength data, reveal about the ammonia distribution and moist convection in the SEB outbreak and northern plumes?  
  > "our ALMA observations provide a crucial, hitherto missing, link in the moist convection theory by showing that ammonia gas from the deep atmosphere is indeed brought up in these plumes." (abstract)
- Target **Jupiter**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.00701.S
- bands: Band 3 (3 mm, 90–105 GHz) and Band 6 (1.3 mm, 223–243 GHz)  
  > "Observations were obtained in Band 3 (3 mm, 90–105 GHz) and Band 6 (1.3 mm, 223–243 GHz)." (2 OBSERVATIONS)
- frequencies and spectral setup: 4 spectral windows per setup, each 2 GHz wide; mosaics of 5 pointings (Band 3) and 17 (Band 6)  
  > "A total of 5 pointings were used in Band 3, and 17 in Band 6" (2.1 ALMA); "In each setup, we had 4 spectral windows, each 2 GHz wide." (2.1 ALMA)
- continuum bandwidth: _not stated_
- arrays: 12-m array only; no ACA short spacings  
  > "in Cycle 4 it was not possible to simultaneously use the Atacama Compact Array (ACA) and the 12-m array" (2.1 ALMA)
- configurations: C40-2, 40 antennas  
  > "when the array was composed of 40 antennas, and placed in a relatively compact configuration (C40-2)" (2 OBSERVATIONS)
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 3-5 January 2017  
  > "Jupiter was observed with ALMA on 3-5 January 2017" (2 OBSERVATIONS)
- pi or archival as stated: _not stated_
- Other facility **VLA**: X-band (~3.5 cm) maps, 11 Dec 2016 and 11 Jan 2017  
  > "Jupiter was observed with the VLA (program 16B-048) on 11 Dec. 2016 and 11 Jan. 2017." (2.2 VLA)
- Other facility **HST WFC3/UVIS**: UV/visible/near-IR images of cloud structure and plumes; wind profile  
  > "Images in the UV/visible/near-IR range were taken on 11 Dec. 2016 (program GO-14661) and 11 Jan. 2017 (program GO-14839 )" (2.3 HST)
- Other facility **VLT/VISIR**: 7-20 micron thermal-IR images  
  > "Thermal-infrared observations in eight narrow-band filters between 7-20 $\mu$m were acquired by the VISIR instrument" (2.4 VLT)
- Other facility **Subaru/COMICS**: 7-20 micron images  
  > "Images of Jupiter at 7-20 $\mu$m were acquired using the COMICS instrument at the Subaru telescope between January 11 and 14, 2017" (2.5 Subaru)
- Other facility **Gemini/NIRI**: 4.68 micron images  
  > "We use the M’ filter, with a central wavelength of 4.68 $\mu$m" (2.6 Gemini)
- Other facility **Keck/NIRSPEC**: 5 micron echelle spectra  
  > "We obtained 5-$\mu$m spectra of Jupiter using NIRSPEC" (2.7 Keck)
- External data: Disk-averaged brightness temperature spectrum and Karim et al. model used to rescale ALMA flux scale  
  > "we assumed disk-averaged brightness temperatures based on the best model fits to dP19’s disk-averaged brightness temperature spectrum (Fig. 4 in dP19, with the Karim et al. (2018) model)" (2.1 ALMA) [from de Pater et al. 2019 (dP19); Karim et al. 2018]
- External data: Best-fit radiative-transfer models to 2013-2014 VLA data, extended to mm wavelengths  
  > "We stress here that no new models were produced; the existing models were merely extended into the mm-wavelength range." (4.1 RT Modeling) [from de Pater et al. 2019 (dP19)]
- External data: Galileo Probe H2O profile (47 ppm)  
  > "we adopted the gaseous H$_2$O profile as measured in the Galileo Probe entry site (Wong et al., 2004)" (4.4 Keck) [from Wong et al., 2004]

## Processing

### Calibration

- pipeline or manual: Initial flagging and calibration with ALMA pipeline in CASA; fluxes rescaled to Callisto  
  > "The initial flagging and calibration was done using the ALMA pipeline in the Common Astronomy Software Applications package, CASA." (2.1 ALMA)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Different flux calibrators per execution; all referenced to Callisto (CASA Butler-JPL-Horizons 2012 model); J1256-0547 phase calibrator  
  > "We modified the flux densities so that all scans were referenced to Callisto, for which we used the internal model in CASA (Butler-Horizons 2012" (2.1 ALMA)
- flux scale uncertainty: _not stated_
- self calibration: Self-calibration as in earlier VLA Jupiter work  
  > "The procedures to produce longitude-smeared and longitude-resolved maps were then similar to those used in earlier VLA observations, including self-calibration" (2.1 ALMA)

### Imaging

- task: MIRIAD used to create maps (CASA mosaicking unreliable at the time)  
  > "The MIRIAD software package (Sault et al., 1995) was used to create maps of the planet" (2.1 ALMA)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Limb-darkened disk subtracted from uv data (Band 3: Tb'=131 K, q=0.10; Band 6: Tb'=115 K, q=0.08), added back later  
  > "Disks which provided a best-fit to the Band 3 (T$_b' =$ 131 K with $q=$ 0.10) and Band 6 (T$_b' =$ 115 K with $q=$ 0.08) data" (2.1 ALMA)
- line free channels: _not stated_
- primary beam correction: Gaussian primary beam, FWHM 1.13 lambda/D, D = 12 m  
  > "ALMA’s primary beam was assumed to be a gaussian with FWHM $1.13\lambda/D$ radians" (2.1 ALMA)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Longitude-smeared/resolved mapping, self-calibration and limb-darkened disk subtraction procedures  
  > "As in the previous papers, in order to best assess small variations on Jupiter’s disk, a limb-darkened disk was subtracted from the u-v data" (2.1 ALMA) [from Sault et al., 2004; dP16, dP19]
- Nominal atmosphere for Radio-BEAR (enhancements, adiabat, TP profile)  
  > "As in dP19, in our nominal atmosphere, assumed to be in thermochemical equilibrium, the abundances of CH$_4$, H$_2$O, and Ar in the deep atmosphere are enhanced by a factor of 4 over the solar values" (RT Modeling of the ALMA Longitude-smeared Maps) [from de Pater et al. 2019 (dP19)]
- Keck NIRSPEC fitting methodology  
  > "the details of our methodology are described by Bjoraker et al. (2018)" (4.4 Keck) [from Bjoraker et al. (2018)]

### Not stated but needed to reproduce (our reading)

- Which calibrators were used in each execution and the exact flux rescaling factors
- Adopted Tb values per band (in image table, not in text)
- Uv-range, cell size, image size, weighting and CLEAN settings for the MIRIAD mosaic imaging
- Self-calibration parameters for ALMA data
- CASA pipeline version
- Final beam sizes and rms noise values (only in tables)
- Exact Radio-BEAR model inputs per latitude from dP19

## Analysis recipe

1. **Calibrate and rescale flux scale**: ALMA pipeline in CASA; fluxes referenced to Callisto; phases adjusted for Jupiter motion  
  > "We modified the phases of Jupiter to take out its motion across the sky." (2.1 ALMA)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Correct low brightness temperature**: Scaled maps to adopted disk-averaged Tb from dP19/Karim model, because Tsys on blank sky underestimated for bright source  
  > "we multiplied the maps by T$_b$(cent)/T$_b'$ and added T$_{\rm cmb}$ to match the observations as close as possible to Jupiter’s disk." (2.1 ALMA)
   - assumption: Disk-averaged Tb follows dP19 best-fit model  
  > "we assumed disk-averaged brightness temperatures based on the best model fits to dP19’s disk-averaged brightness temperature spectrum" (2.1 ALMA)
   - fitting: _not stated_
   - validation: _not stated_
3. **Make longitude-smeared and resolved maps**: Subtract limb-darkened disk, image residuals in MIRIAD with mosaicking and self-calibration, add disk back  
  > "The subtracted disk is added back before we model the data with radiative transfer calculations" (2.1 ALMA)
   - software: MIRIAD
   - parameter: Disk best fit by eye so no planet remains in residual image  
  > "“best fit” means parameters such that there is no planet after imaging the residual u-v data" (2.1 ALMA)
   - fitting: by-eye fit  
  > "a limb-darkened disk was subtracted from the u-v data with a brightness temperature and limb-darkening parameter that produced a best fit (by eye) to the data" (ALMA)
   - validation: _not stated_
4. **Model zonal-mean and feature Tb with RT**: Compare ALMA Tb to Radio-BEAR models fitted to 2013-14 VLA data; interpret deviations as NH3 abundance variations  
  > "We therefore interpret deviations in the ALMA data compared to the model spectrum in terms of variations in the NH$_3$ abundance, and ignore potential effects of cloud opacity." (4.1 RT Modeling)
   - software: Radio-BEAR
   - assumption: Opacity from NH3 only; Tb variations from opacity not temperature; NH3 enhanced 3.2x, 165 K at 1 bar adiabat  
  > "They show that variations in opacity are much more likely than changes in temperature, and therefore, like in dP19, we attribute all changes to variations in opacity." (RT Modeling of the ALMA Longitude-smeared Maps)
   - fitting: no new fits  
  > "We stress here that no new models were produced; the existing models were merely extended into the mm-wavelength range." (RT Modeling of the ALMA Longitude-smeared Maps)
   - validation: Test of NH4SH cloud opacity showed it would lower Tb by a few degrees only with unlikely mass loading  
  > "We tested one case with high NH$_4$SH mass loading ($\sim$1.6 g cm$^{-2}$ between 2.4 and 0.9 bar)" (4.1 RT Modeling)
5. **Model HST and Keck data for plume**: SUNBEAR RT fits to HST I/F spectra; Keck NIRSPEC spectra fitted for clouds, H2O, NH3  
  > "These spectra were fit using our in-house RT code SUNBEAR" (4.3 SEB Outbreak in HST Data)
   - software: SUNBEAR, pydisort
   - fitting: by-hand adjustment of haze opacities, particle radii  
  > "We adapted the opacities and particle radii of these haze layers to fit he spectra." (SEB Outbreak in HST Data)
   - validation: _not stated_

## Software

- **CASA** : ALMA pipeline calibration  
  > "The initial flagging and calibration was done using the ALMA pipeline in the Common Astronomy Software Applications package, CASA." (2.1 ALMA)
- **MIRIAD** : Imaging of ALMA and VLA data  
  > "The MIRIAD software package (Sault et al., 1995) was used to create maps of the planet" (2.1 ALMA)
- **Radio-BEAR** : Radio radiative transfer modeling  
  > "We model our data with the RT code Radio-BEAR (Radio-BErkeley Atmospheric Radiative transfer)" (4.1 RT Modeling of the ALMA Longitude-smeared Maps)
- **SUNBEAR** : UV-to-near-IR RT fits to HST spectra  
  > "These spectra were fit using our in-house RT code SUNBEAR" (4.3 SEB Outbreak in HST Data)
- **pydisort** : Solving radiative transfer within SUNBEAR  
  > "which is fed into `pydisort` to solve the radiative-transfer equation" (4.3 SEB Outbreak in HST Data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Best-fit disk Band 3 | Tb' = 131 K, q = 0.10 | not stated | K | 3 | Band 3 (T$_b' =$ 131 K with $q=$ 0.10) |
| Best-fit disk Band 6 | Tb' = 115 K, q = 0.08 | not stated | K | 3 | Band 6 (T$_b' =$ 115 K with $q=$ 0.08) |
| EZ to radio-hot belt Tb contrast | 22 to 27 K from 3 mm to 1.3 mm | not stated | K | 3 | varies from 22 to 27 K from 3 mm down to 1.3 mm |
| Deep NH3 mole fraction from Keck | 300 ppm at P > 1.2 bar | not stated | ppm | 5 | The best fit was for 300 ppm NH$_3$ for pressures greater than 1.2 bars. |
| Upper-cloud albedo for ED | 12% | not stated | percent | 5 | an upper cloud at 600 mbars with an albedo of 12% |

## Qualitative findings

- Plume source and East Disturbance are dark at 1.3 mm, consistent with NH3 gas rising from the deep atmosphere  
  > "The brightness temperature at 1.3 mm of both the source of the SEB outbreak and the ED is consistent with a model of NH$_3$ gas rising up from the deep atmosphere" (5.2 Moist Convection in the SEB)
- Southern hemisphere zonal structure unchanged 2013 to 2017; northern hemisphere shows a ledge near 17-18N and deeper 23N minimum  
  > "This shows that, averaged over longitude, the southern hemisphere has remained the same over a 3-year period (12/2013–1/2017)." (3.1 Longitude-smeared ALMA Maps)

## Claim tuples

- H: Do SEB outbreak plumes bring up NH3 from the deep atmosphere? | E: ALMA 1.3 and 3 mm maps compared with RT models and multiwavelength data | R: Plume source and ED dark at 1.3 mm, consistent with NH3-rich models | F: Plumes carry deep NH3 aloft, consistent with moist convection | **supported**
- H: Has the NH3 distribution changed since 2013 VLA? | E: Compared ALMA zonal Tb to models fit to 2013-14 VLA | R: Near-perfect match except small differences at some latitudes and a ledge at 18N | F: South unchanged; north NH3 changed near 18N and 26N | **supported**
- H: Do clouds affect mm Tb? | E: RT tests with NH4SH cloud | R: Only an implausibly thick cloud lowers Tb by a few K | F: Cloud opacity can be ignored | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Temperature variations and cloud opacity considered as causes of Tb variations, rejected in favor of NH3 opacity  
  > "They show that variations in opacity are much more likely than changes in temperature" (4.1 RT Modeling)
- How they decided it was enough: _not stated_
- Limitation (authors): Brightness temperatures only 60-70% of expected, attributed to Tsys calibration on blank sky; data scaled  
  > "revealed brightness temperatures that were only of order 60–70% of what we expected" (2.1 ALMA)
- Limitation (authors): Small features are unresolved so Tb are upper limits; missing short spacings  
  > "Because these features are small in angular extent, the measured brightness temperatures should be considered upper limits." (4.2 RT Modeling of the ALMA Longitude-resolved Maps)
- Caveat (inferred, ours): Absolute flux scale depends on an externally imposed Tb rescaling, so absolute NH3 inferences inherit that assumption
- Caveat (inferred, ours): Qualitative model comparison without formal fits or uncertainties
- Caveat (inferred, ours): Keck spectra likely contaminated by hot spots

## Reproducibility

- Data public (paper): ALMA data downloadable from ALMA Archive  
  > "The data can be downloaded from the ALMA Archive." (Acknowledgements)
- Products in archive: _not stated_
- Code: Radio-BEAR on GitHub  
  > "https://github.com/david-deboer/radiobear" (footnote 6)
- Missing: Imaging parameters
- Missing: Rescaling Tb values per execution
- Missing: dP19 model details
- Data volume (inferred): ~100 GB
- Score (inferred): 3/5, Data public and software named, but imaging details and flux rescaling are mostly unstated and results are qualitative.
- Rediscovery candidate: no, Main results are qualitative map comparisons relying on unreleased tables and model inputs.

## Links

- Method: de Pater et al. 2019 (dP19) (VLA mapping and RT modeling method)
- Method: Sault et al. 2004 (Longitude-resolved imaging technique)
- Companion: de Pater et al. 2016 (dP16) (VLA Jupiter maps 2013-2014)
- Related: Juno mission support campaign

## Checks

```json
{
 "quotes": 59,
 "quotes_ok": 59,
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
  "facts": 84,
  "stated": 48,
  "rate": 0.571
 },
 "evidence_ok": true
}
```
