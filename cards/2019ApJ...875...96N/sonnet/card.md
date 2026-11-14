# Dust Continuum Emission and the Upper Limit Fluxes of Submillimeter Water Lines of the Protoplanetary Disk around HD 163296 Observed by ALMA

`2019ApJ...875...96N` | The Astrophysical Journal 2019 | first author: Notsu, Shota | arXiv: 1902.09932 | DOI: 10.3847/1538-4357/ab0ae9

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: Can sub-millimeter water line upper limits toward HD 163296 constrain the mm dust opacity and the extent of the hot water vapor region / H2O snowline position?  
  > "We compare the upper limit fluxes with the values calculated by our models with dust emission included, and we constrain the line emitting region and the dust opacity from the observations." (abstract)
- Target **HD 163296**: coordinates _not stated_; z/distance 101.5 pc  
  > "the distance obtained by Hipparcos measurement in the past ($d\sim$122 pc, e.g., (cite: Perryman1997; vandenAncker1997)) was corrected to $d\sim$101.5 pc (cite: Gaia2018)." (2.2 Target); distance from Gaia DR2 (Gaia Collaboration 2018)  
  > "the distance obtained by Hipparcos measurement in the past ($d\sim$122 pc, e.g., (cite: Perryman1997; vandenAncker1997)) was corrected to $d\sim$101.5 pc (cite: Gaia2018)." (2.2 Target)

## Data provenance

- ALMA projects: 2015.1.01259.S, 2016.1.00884.S, 2013.1.00601.S
- bands: Band 7 (~0.9 mm) new data; Band 6 archival  
  > "The high spatial-resolution continuum and water line observations at Band 7 ($\lambda\sim$0.9 mm) with ALMA was carried out in Cycle 3" (2.1 Observational setup and data reduction)
- frequencies and spectral setup: 4 SPWs, 1.875 GHz each, 1953.125 kHz resolution; centered 320.844, 322.740, 332.844, 334.740 GHz  
  > "The spectral windows were centered at 320.844 GHz (SPW1), 322.740 GHz (SPW2), 332.844 GHz (SPW3), and 334.740 GHz (SPW4)" (2.1 Observational setup and data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: max baseline 2483.5 m, 40 12m antennas  
  > "40 of the 12m antennas were operational and the maximum baseline length was 2483.5m." (2.1 Observational setup and data reduction)
- angular resolution: Band 7: 0.174 x 0.124 arcsec (17.7 x 12.6 au); Band 6: 0.278 x 0.184 arcsec  
  > "The spatial resolutions of the final image is 0.174 $\times$ 0.124 arcsec with a position angle (PA) of 76.799 $\deg$ for Band 7, corresponding to 17.7 au $\times$ 12.6 au." (2.1 Observational setup and data reduction)
- max recoverable scale: _not stated_
- sensitivity: Band 7 rms ~0.1 mJy/beam; Band 6 rms ~0.5 mJy/beam  
  > "The noise level (rms) of the Band 7 image is around 0.1 mJy beam$^{-1}$." (2.1 Observational setup and data reduction)
- time on source: 0.723 hours (43.35 min)  
  > "The integration time on source (HD 163296) is 0.723 hours (43.35 min.)." (2.1 Observational setup and data reduction)
- observing dates: 2016 September 16  
  > "was carried out in Cycle 3 on 2016 September 16 (2015.1.01259.S, PI: S. Notsu)" (2.1 Observational setup and data reduction)
- pi or archival as stated: _not stated_
- Line: ortho-H2 16O 10(2,9)-9(3,6) (321.22568 GHz)
- Line: para-H2 18O 5(1,5)-4(2,2) (322.46517 GHz)
- Line: HDO 3(3,1)-4(2,2) (335.39550 GHz)
- External data: mm dust opacity ~3 cm2/g for HD 163296 and gas-to-dust/gas mass estimates  
  > "the mm dust opacity $\kappa_{\mathrm{mm}}$ is $\sim3$ cm$^{2}$ g$^{-1}$" (2.2 Target) [from (cite: Boneberg2016)]
- External data: Disk inclination ~42 deg  
  > "It has a relatively large inclination angle ($i\sim$42 deg, (cite: Isella2016))" (2.2 Target) [from (cite: Isella2016)]
- External data: Water line parameters from LAMDA (H2 16O) and HITRAN (H2 18O)  
  > "The data for the line parameters are adopted from the Leiden Atomic and Molecular Database LAMDA" (3.1 Upper limit of the water line fluxes) [from (cite: Schoier2005); (cite: Rothman2013)]
- Simulation/model as data: Herbig Ae disk model with water chemistry and RATRAN line profiles (alpha=1e-2, Mdot=1e-8 Msun/yr, g/d=100, M*=2.5 Msun, T*=10000 K), compared with upper limits  
  > "viscous parameter $\alpha$=$10^{-2}$, a mass accretion rate $\dot{M}$=$10^{-8}M_{\bigodot}$ yr$^{-1}$, and gas-to-dust mass ratio $g/d=100$" (3.1 Upper limit of the water line fluxes)

## Processing

### Calibration

- pipeline or manual: CASA calibration of bandpass, gain, absolute flux, then flagging  
  > "after calibration of the bandpass, gain in amplitude and phase, and absolute flux scaling, and then flagging for aberrant data" (2.1 Observational setup and data reduction)
- casa version: CASA 4.7.2  
  > "using the Common Astronomical Software Application (CASA) package, version 4.7.2." (2.1 Observational setup and data reduction)
- pipeline version: _not stated_
- archive products used as is: Band 6 calibrated archival data used  
  > "We also used ALMA Band 6 calibrated archival data (2013.1.00601.S, PI: A. Isella)" (2.1 Observational setup and data reduction)
- flux calibrator: J1733-1304  
  > "J1733-1304 was used for absolute flux calibration." (2.1 Observational setup and data reduction)
- flux scale uncertainty: _not stated_
- self calibration: Self-calibration on continuum; solutions applied to line visibilities  
  > "The obtained solution table of the self-calibration for the continuum emission was applied to the visibilities of the lines." (2.1 Observational setup and data reduction)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs robust 0.5 (Band 7 and Band 6)  
  > "imaged using the CLEAN algorithm with briggs weighting with a robust parameter of 0.5" (2.1 Observational setup and data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Band 7 ACA data combined with 12m data for continuum imaging after phase shift  
  > "we have combined Band 7 archival ACA (Atacama Compact Array) data (2016.1.00884.S, PI: V. Guzman) with our Band 7 data in our dust continuum imaging" (2.1 Observational setup and data reduction)
- smoothing: _not stated_
- final beam: Band 7 0.174x0.124 arcsec PA 76.799; Band 6 0.278x0.184 arcsec PA -87.987  
  > "The spatial resolution of the final image is 0.278 $\times$ 0.184 arcsec with a position angle (PA) of -87.987 $\deg$ for Band 6" (2.1 Observational setup and data reduction)
- final rms: Band 7 ~0.1 mJy/beam; Band 6 ~0.5 mJy/beam  
  > "The noise level (rms) of the calibrated archival data of Band 6 image is around 0.5 mJy beam$^{-1}$." (2.1 Observational setup and data reduction)

### Inherited from earlier work

- Water line model (disk physical/chemical structure and RATRAN line calculations) from earlier papers  
  > "Using these data, we calculated the profiles of water emission lines. For more details, see e.g., (cite: Notsu2015; Notsu2016; Notsu2017; Notsu2018a)." (3.1 Upper limit of the water line fluxes) [from (cite: Notsu2015; Notsu2016; Notsu2017; Notsu2018a)]
- Chemical network  
  > "The large chemical network (cite: Woodall2007; Walsh2010; Walsh2012; Walsh2015) we use to calculate the disk molecular abundances" (3.1 Upper limit of the water line fluxes) [from (cite: Woodall2007; Walsh2010; Walsh2012; Walsh2015)]
- Matched filter method  
  > "(cite: Loomis2018) recently proposed a new method to detect the weak line emissions from Keplerian rotating disks using observed visibility data (matched filter analysis)." (3.2 Matched filtering analysis) [from (cite: Loomis2018)]

### Not stated but needed to reproduce (our reading)

- Self-calibration solution intervals, number of iterations and references
- Line-free channels / continuum subtraction method for spectral cubes
- Cell size, image size, masks, clean threshold
- Number of ACA execution blocks and relative weighting in combination
- Source position, PA used for the Keplerian filter and aperture center
- How rms of peak flux density was measured for 3 sigma limits
- Spectral line cube production details at 1.9 km/s resolution
- Band 6 data processing details (calibration script version)

## Analysis recipe

1. **Calibrate and image Band 7 data**: CASA calibration, Briggs CLEAN robust 0.5, continuum self-cal applied to lines; ACA combined for continuum  
  > "In addition to the usual CLEAN imaging, we performed self-calibration of the continuum emission to improve the sensitivity and image quality." (2.1 Observational setup and data reduction)
   - software: CASA
   - parameter: robust = 0.5  
  > "briggs weighting with a robust parameter of 0.5" (2.1 Observational setup and data reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive 3-sigma upper limits of water line fluxes**: Integrate line flux within 20 au circular aperture; velocity width of 30 km/s assumed for total flux  
  > "we integrate the line flux components within 20 au (circular aperture) from the central star." (Table 1)
   - software: CASA
   - parameter: velocity resolution 1.9 km/s; line width 30 km/s  
  > "we assume that the velocity width of the double peaked profiles is 30 km s$^{-1}$" (3.1 Upper limit of the water line fluxes)
   - assumption: Double-peaked profile width 30 km/s from model profiles  
  > "on the basis of the velocity width of model calculated line profiles" (3.1 Upper limit of the water line fluxes)
   - fitting: _not stated_
   - validation: Matched filter analysis confirms non-detection  
  > "We confirm the non-detection of all three lines as also found in the image-plane analyses." (3.2 Matched filtering analysis)
3. **Model line profiles with varying dust opacity and water-vapor outer edge**: Modified 1D RATRAN with disk chemical model; dust opacity x1, 2, 3, 10; outer edge 5, 8, 11, 14, 20 au; dust continuum subtracted  
  > "We calculate the model line profiles with different dust opacity values and different outer edges of the region with a high water vapor abundance." (3.1 Upper limit of the water line fluxes)
   - software: RATRAN
   - parameter: OPR=3, 16O/18O=560, kappa_mm original 1.0 cm2/g  
  > "We set the isotope ratio of oxygen $^{16}$O/$^{18}$O to 560 throughout the disk" (3.1 Upper limit of the water line fluxes)
   - assumption: No jets/disk winds; no deuterium chemistry so HDO not modeled  
  > "We do not include emission from jet components and disk winds in calculating the line profiles." (3.1 Upper limit of the water line fluxes)
   - fitting: _not stated_
   - validation: _not stated_
4. **Compare limits with models to constrain kappa_mm and snowline**: Compare observed 3 sigma limits with model peak flux densities  
  > "we consider that the mm dust opacity $\kappa_{\mathrm{mm}}$ is larger than 2.0 cm$^{2}$ g$^{-1}$ to explain the water line upper limit" (3.1 Upper limit of the water line fluxes)
   - fitting: _not stated_
   - validation: _not stated_
5. **Dust continuum maps and radial profiles**: Band 7 and Band 6 images, azimuthally averaged radial profiles, spectral index from total fluxes  
  > "we plot the azimuthally-averaged radial profiles of the dust continuum emission in Figure [7]" (4)
   - software: CASA
   - fitting: _not stated_
   - validation: Compared with Isella2016 and Dent2019  
  > "The positions of bright rings and dark gaps in our observed Band 7 data are consistent with those indicated by the previous Cycle 2 observation" (4)

## Software

- **CASA** 4.7.2: calibration and CLEAN imaging  
  > "The visibility data were reduced and calibrated using the Common Astronomical Software Application (CASA) package, version 4.7.2." (2.1 Observational setup and data reduction)
- **RATRAN** : modified 1D code for water line profile calculation  
  > "For the calculation of line profiles, we modified the 1D code RATRAN" (3.1 Upper limit of the water line fluxes)
- **VISIBLE** : matched filter analysis in uv plane  
  > "The matched filter tool VISIBLE [^7] then cross-correlates the transformation of this filter in the $uv$ plane with the visibility data points" (3.2 Matched filtering analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 3 sigma peak flux density ortho-H2 16O 321 GHz | <8.7 | not stated | mJy | 2 | / 1861.2 / $<$ 8.7              / $<$ 5.3$\times$$10^{-21}$ / |
| 3 sigma peak flux density para-H2 18O 322 GHz | <13.9 | not stated | mJy | 2 | / 467.9 / $<$ 13.9              / $<$ 8.5$\times$$10^{-21}$ / |
| 3 sigma peak flux density HDO 335 GHz | <7.3 | not stated | mJy | 2 | / 335.3 / $<$ 7.3              / $<$ 6.3$\times$$10^{-21}$ / |
| 3 sigma total flux ortho-H2 16O / para-H2 18O / HDO | <5.3e-21 / <8.5e-21 / <6.3e-21 | not stated | W m^-2 | 2 | $<$ 5.3$\times$$10^{-21}$ |
| Total disk flux Band 7 / Band 6 | 1.85 / 0.68 | not stated | Jy | 5 | The total disk fluxes are 1.85Jy in Band 7, and 0.68Jy in Band 6, giving spectral index $\alpha_{\mathrm{mm}}$ of $\sim2.7$. |
| Spectral index alpha_mm | ~2.7 | not stated | dimensionless | 5 | giving spectral index $\alpha_{\mathrm{mm}}$ of $\sim2.7$ |
| Lower limit mm dust opacity | >2.0 | not stated | cm2 g-1 | 4 | the mm dust opacity $\kappa_{\mathrm{mm}}$ is larger than 2.0 cm$^{2}$ g$^{-1}$ |

## Qualitative findings

- Three gaps at ~50, 83, 137 au seen in Band 7 continuum, consistent with earlier work  
  > "There are three prominent gaps at around 50, 83 and 137 au" (4)

## Claim tuples

- H: Do the water line non-detections constrain mm dust opacity? | E: Compare 3 sigma upper limits with models at kappa x1,2,3,10 | R: Upper limit of ortho line close to model with 2x opacity; para limit above original model | F: kappa_mm > 2.0 cm2/g if vapor region and snowline beyond 8 au | **supported**
- H: Does the snowline position follow from the para-H2 18O line? | E: Vary outer edge of water vapor region with kappa=2.0 | R: Models with edge at 20 au compared with limits | F: Snowline inside 20 au for kappa_mm=2.0 | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Observation time was ~20% of the requested time, insufficient to test the model  
  > "the observation time executed (20% of our proposed time in our Cycle 3 proposal) was not enough to test our model." (3.1 Upper limit of the water line fluxes)
- Caveat (inferred, ours): Constraints are conditional on a single fiducial disk model and an assumed water-vapor outer edge
- Caveat (inferred, ours): Upper limits depend on the assumed 30 km/s line width, which the authors say may overestimate them
- Caveat (inferred, ours): Dust opacity constraint degenerate with gas-to-dust ratio and grain properties

## Reproducibility

- Data public (paper): Data cited by project codes, archival Band 6 and ACA data  
  > "Band 7 archival ACA (Atacama Compact Array) data (2016.1.00884.S, PI: V. Guzman)" (2.1 Observational setup and data reduction)
- Products in archive: _not stated_
- Code: VISIBLE is publicly available (github); the authors' modified RATRAN/disk model code not stated as released  
  > "freely available at <https://github.com/AstroChem/VISIBLE>" (footnote 7)
- Missing: Modified RATRAN code and chemical model outputs
- Missing: Self-calibration and cube imaging parameters
- Missing: Details of upper limit rms measurement
- Data volume (inferred): ~50-100 GB raw for the three projects
- Score (inferred): 3/5, Data public and basic imaging described, but model code from earlier papers and many imaging parameters are missing.
- Rediscovery candidate: no, Main results depend on an unreleased disk chemistry and radiative transfer model; the observed numbers are limits.

## Links

- Method: (cite: Loomis2018) (matched filter method)
- Method: (cite: Notsu2017) (water line model of Herbig Ae disk)
- Companion: (cite: Notsu2016) (Paper I of the series)
- Companion: (cite: Notsu2018a) (Paper III of the series)
- Related: DSHARP

## Checks

```json
{
 "quotes": 61,
 "quotes_ok": 61,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 76,
  "stated": 45,
  "rate": 0.592
 },
 "evidence_ok": true
}
```
