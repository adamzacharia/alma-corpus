# JWST Edge-on Disk Ice (JEDIce): Program Overview and Ice Survey Results

`2026ApJ..1002...17B` | The Astrophysical Journal 2026 | first author: Bergner, Jennifer B. | arXiv: 2603.18163 | DOI: 10.3847/1538-4357/ae5961

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type multi_facility_alma_minor

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: Understand the range of ice compositions in edge-on protoplanetary disks and how ice inventory and spatial distribution relate to other disk properties (ALMA used only for millimeter continuum context images)  
  > "The primary motivation for this program is to understand the range of possible ice compositions in protoplanetary disks, and how the ice inventory and spatial distribution are related to other disk properties." (1 Introduction)
- Target **HV Tau C**: coordinates 04:38:35.51, +26:10:41.32 (J2000)  
  > "HV Tau C | 04:38:35.51, +26:10:41.32 | Taurus | 84 | 140 | M0 | 1,7" (Table 1); z/distance 140 pc  
  > "HV Tau C | 04:38:35.51, +26:10:41.32 | Taurus | 84 | 140 | M0 | 1,7" (Table 1); distance from Table 1 references 1,7 (cite: Stapelfeldt2003), (cite: Villenave2020); which reference gives the distance is not stated  
  > "HV Tau C | 04:38:35.51, +26:10:41.32 | Taurus | 84 | 140 | M0 | 1,7" (Table 1)
- Target **Oph 163131**: coordinates 16:31:31.25, -24:26:28.47 (J2000)  
  > "Oph 163131 | 16:31:31.25, -24:26:28.47 | $\rho$ Oph | 84 | 120 | K4 | 2,7" (Table 1); z/distance 120 pc  
  > "Oph 163131 | 16:31:31.25, -24:26:28.47 | $\rho$ Oph | 84 | 120 | K4 | 2,7" (Table 1); distance from Table 1 references 2,7 (cite: Wolff2021), (cite: Villenave2020); which reference gives the distance is not stated  
  > "Oph 163131 | 16:31:31.25, -24:26:28.47 | $\rho$ Oph | 84 | 120 | K4 | 2,7" (Table 1)
- Target **Flying Saucer**: coordinates 16:28:13.69, -24:31:39.48 (J2000)  
  > "Flying Saucer | 16:28:13.69, -24:31:39.48 | $\rho$ Oph | 86 | 120 | M1 | 3,8" (Table 1); z/distance 120 pc  
  > "Flying Saucer | 16:28:13.69, -24:31:39.48 | $\rho$ Oph | 86 | 120 | M1 | 3,8" (Table 1); distance from Table 1 references 3,8 (cite: Grosso2003), (cite: Guilloteau2016); which reference gives the distance is not stated  
  > "Flying Saucer | 16:28:13.69, -24:31:39.48 | $\rho$ Oph | 86 | 120 | M1 | 3,8" (Table 1)
- Target **ESO-Halpha 574**: coordinates 11:16:02.76, -76:24:53.24 (J2000)  
  > "ESO-H$\alpha$ 574 | 11:16:02.76, -76:24:53.24 | Cham I | 80 | 192 | K8 | 4,7" (Table 1); z/distance 192 pc  
  > "ESO-H$\alpha$ 574 | 11:16:02.76, -76:24:53.24 | Cham I | 80 | 192 | K8 | 4,7" (Table 1); distance from Table 1 references 4,7 (cite: Stapelfeldt2014), (cite: Villenave2020); which reference gives the distance is not stated  
  > "ESO-H$\alpha$ 574 | 11:16:02.76, -76:24:53.24 | Cham I | 80 | 192 | K8 | 4,7" (Table 1)
- Target **LkHalpha 263C**: coordinates 02:56:08.67, +20:03:40.60 (J2000)  
  > "LkH$\alpha$ 263C | 02:56:08.67, +20:03:40.60 | L1457 | 87 | 275 | M0 | 5" (Table 1); z/distance 275 pc  
  > "LkH$\alpha$ 263C | 02:56:08.67, +20:03:40.60 | L1457 | 87 | 275 | M0 | 5" (Table 1); distance from Table 1 reference 5 (cite: Jayawardhana2002); not stated whether this gives the distance. No ALMA data used for this target.  
  > "LkH$\alpha$ 263C | 02:56:08.67, +20:03:40.60 | L1457 | 87 | 275 | M0 | 5" (Table 1)
- Target **OphE MM3**: coordinates 16:27:05.86, -24:37:08.36 (J2000)  
  > "OphE MM3 | 16:27:05.86, -24:37:08.36 | $\rho$ Oph | 87 | 120 | K5 | 6" (Table 1); z/distance 120 pc  
  > "OphE MM3 | 16:27:05.86, -24:37:08.36 | $\rho$ Oph | 87 | 120 | K5 | 6" (Table 1); distance from Table 1 reference 6 (cite: Brandner2000); not stated whether this gives the distance. NIRSpec data not yet obtained and no ALMA data used.  
  > "OphE MM3 | 16:27:05.86, -24:37:08.36 | $\rho$ Oph | 87 | 120 | K5 | 6" (Table 1)

## Data provenance

- ALMA projects: 2023.1.00634.S, 2016.1.00771.S, 2023.1.00907.S, 2022.1.01302.S
- bands: Band 6 or 7  
  > "along with the millimeter continuum observed with ALMA Band 6 or 7 when available" (3.1 Continuum images)
- frequencies and spectral setup: Continuum at HV Tau C 284 GHz, Oph 163131 224 GHz, Flying Saucer 347 GHz, ESO-Halpha 574 225 GHz  
  > "2023.1.00634.S (HV Tau C, 284 GHz), 2016.1.00771.S (Oph 163131, 224 GHz), 2023.1.00907.S (Flying Saucer, 347 GHz), and 2022.1.01302.S (ESO-H$\alpha$ 574, 225 GHz)" (3.1 Continuum images)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Retrieved from the ALMA Science Archive (archival)  
  > "The millimeter continuum data were retrieved from the ALMA Science Archive" (3.1 Continuum images)
- Line: H2O ice OH stretch at 3 micron (JWST, not ALMA) (not stated (wavelength 3 micron))
- Line: CO2 ice stretch at 4.27 micron (JWST, not ALMA) (not stated (wavelength 4.27 micron))
- Line: CO ice stretch at 4.67 micron (JWST, not ALMA) (not stated (wavelength 4.67 micron))
- Other facility **JWST NIRSpec/IFU**: 1.66-5.27 micron IFU spectra, G235H/F170LP and G395H/F290LP, R~2700 (primary data of the paper)  
  > "The NIRSpec/IFU observations, taken with the G235H/F170LP and G395H/F290LP grating/filter combinations, cover 1.66–5.27 $\mu$m with a spectral resolving power of $\sim$2700." (2.2 Observations)
- Other facility **JWST MIRI/MRS**: 4.90-27.9 micron IFU spectra, R 1330 to 3710; HV Tau C and Flying Saucer from Program #1282  
  > "cover 4.90–27.9 $\mu$m with a spectral resolving power ranging from 1330 to 3710." (2.2 Observations); "The exception is MIRI/MRS observations of HV Tau C and Flying Saucer, which were available as part of JWST Program #1282" (2.2 Observations)
- External data: MIRI/MRS observations of HV Tau C and Flying Saucer from JWST Program #1282  
  > "which were available as part of JWST Program #1282 (PI: T. Henning;" (2.2 Observations) [from (cite: Henning2024)]
- External data: Reference 15 K pure H2O ice transmission spectrum, via LIDA  
  > "all correspond to 15 K pure ices and were taken from (cite: Oberg2007) (H$_2$O)" (2.5 Global optical depth spectra) [from (cite: Oberg2007); LIDA (cite: Rocha2022)]
- External data: Reference 15 K pure CO2 and CO ice transmission spectra, via LIDA  
  > "and (cite: vanBroekhuizen2006) (CO$_2$, CO) via the Leiden Ice Database for Astrochemistry" (2.5 Global optical depth spectra) [from (cite: vanBroekhuizen2006); LIDA (cite: Rocha2022)]
- External data: PAH template spectrum of the HD 97300 disk observed with Spitzer  
  > "The PAH template corresponds to the spectrum of the HD 97300 disk observed with *Spitzer* and shown in (cite: Dartois2025)." (2.5 Global optical depth spectra) [from (cite: Dartois2025)]
- External data: Lab-measured spectral profiles of pure CO, CO:CO2 and CO:H2O ices (formed and measured at 10 K) compared with observed CO bands  
  > "with all ices formed at 10 K and spectra measured at 10 K (cite: Bergner2024)." (4.1.2 Ice band profiles) [from (cite: Bergner2024)]
- External data: Optical constants for pyroxene stoichiometry silicate  
  > "with optical constants from (cite: Dorschner1995) for a pyroxene stoichiometry" (2.5 Global optical depth spectra) [from (cite: Dorschner1995)]
- External data: Disk inclinations, distances and spectral types listed in Table 1  
  > "Table notes: $^{}$ (1) (cite: Stapelfeldt2003), (2) (cite: Wolff2021) (3) (cite: Grosso2003) (4) (cite: Stapelfeldt2014) (5) (cite: Jayawardhana2002) (6) (cite: Brandner2000) (7) (cite: Villenave2020) (8) (cite: Guilloteau2016)" (Table 1) [from (cite: Stapelfeldt2003; Wolff2021; Grosso2003; Stapelfeldt2014; Jayawardhana2002; Brandner2000; Villenave2020; Guilloteau2016)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: JWST calibration pipeline versions and CRDS contexts per cube are given in Table 3 (JWST only; no ALMA calibration described)  
  > "The JWST calibration pipeline versions and calibration reference contexts used for each cube are listed in Table" (2.3 Data preparation)
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
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

### Inherited from earlier work

- MIRI processing with the JDISCS pipeline and 1D spectrum extraction from stage 2b cubes  
  > "The MIRI observations were processed using the JWST Disk Infrared Spectral Chemistry Survey (JDISCS) pipeline described in (cite: Pontoppidan2024)." (2.3 Data preparation); "One-dimensional MIRI spectra were extracted from the stage 2b cubes as described in (cite: Pontoppidan2024)." (2.3 Data preparation) [from (cite: Pontoppidan2024)]
- Continuum estimation method inspired by earlier work  
  > "special care was taken to estimate the continuum in each spectrum, using a method inspired by (cite: Pontoppidan2024)." (2.3 Data preparation) [from (cite: Pontoppidan2024)]
- Lab CO ice profiles used for comparison taken from earlier work  
  > "with all ices formed at 10 K and spectra measured at 10 K (cite: Bergner2024)." (4.1.2 Ice band profiles) [from (cite: Bergner2024)]

### Not stated but needed to reproduce (our reading)

- ALMA array configurations, baselines, angular resolution, sensitivity and observing dates for the four ALMA projects are not given
- ALMA calibration (CASA/pipeline version, flux calibrator) and imaging parameters (task, weighting, robust, cell, image size, beam, rms) are not given
- Which of the four ALMA projects' execution blocks or products were used, and whether archive products were used as is
- How the JWST and ALMA images were registered beyond 'aligned by eye'
- Median-filter kernel sizes, flagging thresholds, number of iterations and Savitzky-Golay window/order used for continuum and gas-line removal (kernel sizes varied by wavelength range but are not listed)
- Exact polynomial order for global continuum fit
- Version numbers of Matplotlib, NumPy, SciPy, Astropy and optool
- Exact JWST observation IDs/MAST product names beyond program numbers 5299 and 1282

## Analysis recipe

1. **compare near-IR and ALMA millimeter continuum**: JWST and ALMA continuum images aligned by eye on continuum centers and compared morphologically  
  > "To mitigate small pointing discrepancies, the JWST and ALMA images were aligned by eye based on their continuum centers." (3.1 Continuum images)
   - fitting: _not stated_
   - validation: _not stated_
2. **extract and scale 1D spectra**: NIRSpec 1D spectra extracted from stage 3 cubes with a fixed elliptical aperture per disk; G395H taken as flux reference and neighboring settings scaled by median flux in overlapping wavelengths  
  > "we adopted the G395H setting as our reference for absolute fluxes." (2.3 Data preparation); "the fluxes of each neighboring spectral setting were scaled in turn, based on the median flux level measured within the overlapping wavelength range of adjacent settings." (2.3 Data preparation)
   - software: JWST calibration pipeline
   - parameter: Aperture chosen to encompass continuum emission at >5 sigma; aperture sizes in Table 3  
  > "using a fixed elliptical aperture chosen for each disk to encompass the continuum emission at a $>$5$\sigma$ level" (2.3 Data preparation)
   - assumption: Extractions are affected by aperture losses because the disks are extended  
  > "Since the disks are extended, extractions of one-dimensional spectra are affected by various degrees of aperture-losses." (2.3 Data preparation)
   - fitting: _not stated_
   - validation: _not stated_
3. **model the smoothed continuum and remove gas lines**: Iterative median filtering with decreasing flagging threshold and interpolation over flagged channels, then Savitzky-Golay smoothing; global continuum from polynomial fit to featureless regions  
  > "(i) a median filter was applied to the spectrum, (ii) channels in which the flux deviated from the local median by more than a specified threshold were flagged" (2.3 Data preparation); "After this, the spectrum was smoothed using Savitzky-Golay filtering." (2.3 Data preparation); "made by fitting a polynomial continuum (shown in Figure [2](#fig:spec_nmir)) to featureless regions across the entire near- to mid-IR" (3.4 Global optical depth spectra)
   - parameter: Kernel sizes adjusted per wavelength range; continuum fit regions listed in Table 4  
  > "kernel sizes in different wavelength ranges of the spectrum were adjusted to achieve a smoothly varying continuum without removing true ice absorption features." (2.3 Data preparation)
   - fitting: _not stated_
   - validation: Choice of continuum model said not to affect which features are present  
  > "the choice of continuum model does not affect our conclusions about what features are present in the disk spectra." (3.4 Global optical depth spectra)
4. **compute local ice optical depth spectra**: Optical depth from -ln(F/F_cont) with F_cont a local continuum model over baseline regions  
  > "These are calculated from $-\mathrm{ln}(F/F_\mathrm{cont})$, where $F$ is the observed flux and $F_\mathrm{cont}$ is the local continuum model." (4.1.1 Absolute optical depths)
   - assumption: Observable is not a true line-of-sight optical depth because of radiative transfer effects  
  > "Note that this observable is not a true line-of-sight optical depth due to radiative transfer effects" (4.1.1 Absolute optical depths)
   - fitting: _not stated_
   - validation: _not stated_
5. **map peak ice optical depth across the disks**: Per-pixel local optical depth spectra for pixels with median flux at least 3x the off-source noise; peak optical depth per pixel normalized by the image maximum  
  > "optical depths were measured for all pixels where the median flux is at least 3$\times$ the off-source noise level within the wavelength range of the band" (4.1.3 Optical depth maps); "The peak optical depth in each pixel was divided by the highest value across the image" (4.1.3 Optical depth maps)
   - parameter: Band ranges: 2.68-3.60 micron H2O, 4.19-4.33 micron CO2, 4.65-4.71 micron CO  
  > "for which we adopt 2.68–3.60 $\mu$m for H$_2$O, 4.19–4.33 $\mu$m for CO$_2$, and 4.65–4.71 $\mu$m for CO" (4.1.3 Optical depth maps)
   - fitting: _not stated_
   - validation: Non-zero CO optical depth beyond the Flying Saucer transition taken to show it is not a low-S/N artifact  
  > "The fact that the CO optical depth does not drop to zero beyond this transition confirms that it is not an artifact due to low signal-to-noise." (4.1.3 Optical depth maps)
6. **identify CO ice mixing environment**: Visual comparison of observed CO band profiles with lab profiles of pure CO, CO:CO2 and CO:H2O ices  
  > "The apolar CO:CO$_2$ mixture clearly provides the best match to the widths and peak positions of the observed CO band profiles." (4.1.2 Ice band profiles)
   - assumption: CO band profile is much less sensitive to radiative transfer effects than CO2 and H2O, based on prior models  
  > "the CO band profile is much less sensitive to radiative transfer effects in edge-on disks, with models showing only slight differences compared to thin film band profiles (cite: Bergner2024)." (4.1.2 Ice band profiles)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **JWST calibration pipeline** 1.15.1 to 1.18.0 depending on cube (Table 3): Calibration of NIRSpec cubes to stage 3 and MIRI cubes  
  > "The NIRSpec cubes were reduced using the JWST calibration pipeline to stage 3." (2.3 Data preparation)
- **JDISCS pipeline** : Processing of the MIRI observations  
  > "The MIRI observations were processed using the JWST Disk Infrared Spectral Chemistry Survey (JDISCS) pipeline described in (cite: Pontoppidan2024)." (2.3 Data preparation)
- **optool** : Illustrative silicate absorption profile (0.005-5 micron grain sizes, pyroxene optical constants)  
  > "in size, generated with `optool` (cite: Dominik2021)" (3.4 Global optical depth spectra)
- **Leiden Ice Database for Astrochemistry (LIDA)** : Source of reference ice transmission spectra  
  > "via the Leiden Ice Database for Astrochemistry (LIDA; (cite: Rocha2022))" (3.4 Global optical depth spectra)
- **Matplotlib** : _not stated_
- **NumPy** : _not stated_
- **SciPy** : _not stated_
- **Astropy** : _not stated_

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Peak optical depth, H2O ice band | ~0.3-0.8 | not stated | dimensionless | 4 | The peak optical depths range from $\sim$0.3–0.8 for H$_2$O, 0.3–0.9 for the CO$_2$ stretch, and 0.05–0.3 for CO. |
| Peak optical depth, CO2 stretch | 0.3-0.9 | not stated | dimensionless | 4 | The peak optical depths range from $\sim$0.3–0.8 for H$_2$O, 0.3–0.9 for the CO$_2$ stretch, and 0.05–0.3 for CO. |
| Peak optical depth, CO ice band | 0.05-0.3 | not stated | dimensionless | 4 | The peak optical depths range from $\sim$0.3–0.8 for H$_2$O, 0.3–0.9 for the CO$_2$ stretch, and 0.05–0.3 for CO. |
| Peak optical depth, CO2 bend (most disks) | ~0.1-0.3 (Flying Saucer ~0.5, low S/N) | not stated | dimensionless | 4 | For most disks, the CO$_2$ bend has a peak optical depth around 0.1–0.3. Flying Saucer is the exception, with an apparent optical depth around 0.5 |
| Variation of peak optical depth for a given ice band across the sample | factors of ~3-6 | not stated | dimensionless | 4 | our sample contains a fairly wide range of absolute optical depths for a given ice band (varying by factors of $\sim$3–6) |
| Peak optical depth of 4.6 micron OCN- feature in HV Tau C | ~0.05 | not stated | dimensionless | 4 | The feature is deepest for HV Tau C, with a peak optical depth of $\sim$0.05 |
| Flying Saucer CO optical depth above and below transition at projected elevation 0.3 arcsec | ~0.4 to ~0.1 | not stated | dimensionless | 5 | CO exhibits a sharp transition from a high optical depth ($\sim$0.4) to a low optical depth ($\sim$0.1) at a projected elevation of 0.3$''$. |
| G235H flux relative to G395H in overlap | higher by 1-10% | not stated | percent | 2 | The G235H fluxes were higher than the G395H fluxes by factors of 1–10%. |
| MIRI flux relative to G395H | lower by 20-30%; Oph 163131 1.8x lower; Flying Saucer 4.5x lower | not stated | percent / factor | 2 | The MIRI fluxes were lower than the G395H fluxes by 20–30%, except for Oph 163131 (1.8$\times$ lower) and Flying Saucer (4.5$\times$ lower). |
| Disks with OCN- detection | 4 of 5 | not stated | count | 4 | OCN$^-$ is a common trace ice component with a detection in 4 of the 5 disks. |

## Qualitative findings

- H2O, CO2 and CO ices detected toward all five disks, with ice features across the full region where IR continuum is detected, implying vertically elevated icy grains are common  
  > "The major ice species H$_2$O, CO$_2$, and CO are detected towards all disks" (abstract); "vertically elevated ice grains therefore seem to be ubiquitous in disks." (abstract)
- The millimeter continuum has much smaller vertical extent than the near-IR continuum in all cases, interpreted as vertical settling of mm grains  
  > "In all cases, the millimeter continuum has a much smaller vertical extent than the near-IR continuum" (3.1 Continuum images); "This is explained by efficient vertical settling of large mm-sized grains to the midplane" (3.1 Continuum images)
- CO ice is dominated by apolar CO:CO2 mixtures in all disks  
  > "The CO ice is consistently dominated by apolar CO:CO$_2$ mixtures" (abstract)

## Claim tuples

- H: Do edge-on disks show ice features at all vertical heights where IR continuum is detected? | E: Normalized peak optical depth maps of H2O, CO2 and CO bands from NIRSpec IFU cubes | R: A measurable optical depth for each ice band across virtually the entire continuum region in all disks | F: Vertically elevated icy grains are the norm for protoplanetary disks | **supported**
- H: In what environment is CO ice in the disks (pure, polar H2O mixture or apolar CO2 mixture)? | E: Compare observed CO band profiles with lab profiles of pure CO, CO:CO2 and CO:H2O ices | R: CO:CO2 matches widths and peak positions; CO:H2O is much broader and pure CO much narrower | F: Disk CO ice is predominantly an apolar mixture with CO2, so ices are neither fully inherited nor reset | **supported**
- H: Do ice abundances and compositions differ among disks? | E: Compare peak optical depths and band ratios of H2O, CO2 and CO across five disks | R: Peak optical depths vary by factors of ~3-6 and relative band depths also vary | F: Suggests a range of ice abundances and compositions, but radiative transfer modeling is needed to quantify | **partially**
- H: Are small protostellar ice molecules and ammonium-salt tracers present in disk ices? | E: Search of trace ice spectral regions for CH4, NH3, CH3OH, OCN-, 6.85 micron band | R: CH4, NH3, CH3OH generally not detected; OCN- detected in 4 of 5 disks | F: Disk ices may be evolving toward comet-like compositions | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Empirical analysis chosen because radiative transfer effects perturb ice features and modeling is left to future work  
  > "we focus here on what can be learned with an empirical approach." (4 Ice survey results)
- Alternative: OCN- and SO2 considered unlikely main carriers of the 7.7 micron feature in HV Tau C because their peaks are red-shifted from the observed absorption  
  > "we consider them unlikely to be the main carriers." (4.2.2 7.7 micron)
- How they decided it was enough: _not stated_
- Limitation (authors): Observed optical depth cannot be converted directly into line-of-sight ice column density  
  > "therefore cannot be directly converted to a line-of-sight ice column density" (4.1.1 Absolute optical depths)
- Limitation (authors): NIRSpec observations of OphE MM3 not obtained because of failed guide-star acquisition  
  > "Due to a failed guide-star acquisition, NIRSpec observations of OphE MM3 have not yet been obtained." (2.2 Observations)
- Limitation (authors): Low S/N in mid-IR for Flying Saucer and LkHalpha 263C makes mid-IR absorption features harder to interpret  
  > "makes it somewhat more challenging to interpret the depth and shape of mid-IR absorption features in these disks." (3.4 Global optical depth spectra)
- Caveat (inferred, ours): ALMA data are used only qualitatively as context images with eye-aligned overlays; no ALMA measurements are reported
- Caveat (inferred, ours): Ice band identification is by visual comparison with lab spectra, with no quantitative fit statistics
- Caveat (inferred, ours): Optical depth conclusions are empirical and uncorrected for radiative transfer effects
- Caveat (inferred, ours): Flux scaling between NIRSpec and MIRI settings is uncertain for Oph 163131 and Flying Saucer (factors up to 4.5)

## Reproducibility

- Data public (paper): ALMA data retrieved from the ALMA Science Archive; JWST data from MAST  
  > "The millimeter continuum data were retrieved from the ALMA Science Archive" (3.1 Continuum images); "The data were obtained from the Mikulski Archive for Space Telescopes at the Space Telescope Science Institute" (Acknowledgements)
- Products in archive: _not stated_
- Code: _not stated_
- Missing: ALMA calibration and imaging recipe and products
- Missing: Continuum/gas-line filtering kernel sizes and thresholds
- Missing: Machine-readable ice band measurements per disk
- Missing: Software versions
- Data volume (inferred): JWST NIRSpec and MIRI IFU cubes for five disks (several GB to tens of GB) plus four small ALMA continuum datasets (a few GB each if raw)
- Score (inferred): 3/5, JWST and ALMA data are public and the JWST reduction and continuum steps are described in outline, but many filter parameters and the ALMA processing are unstated, and results are mostly ranges from figures.
- Rediscovery candidate: no, ALMA plays a minor role, ALMA processing is not given, and key results are qualitative or approximate ranges rather than precise numbers.

## Links

- Method: (cite: Pontoppidan2024) (JDISCS pipeline for MIRI processing, 1D extraction and continuum method)
- Companion: (cite: Bergner2024) (Radiative transfer modeling and CO ice mixing analysis for HH 48 NE; lab CO ice profiles)
- Companion: (cite: Henning2024) (JWST Program #1282 MIRI/MRS data for HV Tau C and Flying Saucer)
- Companion: (cite: Sturm2023c) (First near-/mid-IR JWST observations of an edge-on disk, HH 48 NE)
- Related: JWST Program #5299 (JEDIce)
- Related: JWST Program #1282
- Related: JWST Disk Infrared Spectral Chemistry Survey (JDISCS)

## Checks

```json
{
 "quotes": 96,
 "quotes_ok": 96,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 110,
  "stated": 62,
  "rate": 0.564
 },
 "evidence_ok": true
}
```
