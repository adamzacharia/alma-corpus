# The AGN fuelling/feedback cycle in nearby radio galaxies I. ALMA observations and early results

`2019MNRAS.484.4239R` | Monthly Notices of the Royal Astronomical Society 2019 | first author: Ruffa, Ilaria | arXiv: 1901.07513 | DOI: 10.1093/mnras/stz255

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: What are the molecular gas and 230 GHz continuum (core and jet) properties of nearby LERGs, and how do the gas discs relate to the radio jets, to inform the AGN fuelling/feedback cycle?  
  > "We are conducting an extensive study of different galaxy components (stars, warm and cold gas, radio jets) with the aim of improving our understanding of the AGN fuelling/feedback cycle in LERGs." (abstract)
- Target **Nine southern LERGs (IC 1531, NGC 612, PKS 0718-34, NGC 3100, NGC 3557, ESO 443-G 024, IC 4296, NGC 7075, IC 1459)**: coordinates _not stated_; z/distance z = 0.0047-0.0298 for the sample; luminosity distances 25.9-130.4 Mpc for the observed targets (e.g. NGC 3100 z=0.0088, D_L=38.0 Mpc)  
  > "PKS 0958$-$314 | NGC 3100 | 0.0088 | 0.5 | 23.0 | I | 38.0 | 2629$\pm$20" (Table 1); "(3) Galaxy redshift taken from the NASA/IPAC extragalactic database (NED)." (Table 1); distance from Redshift from NED; D_L derived assuming H0=70, OmegaL=0.7, OmegaM=0.3  
  > "PKS 0958$-$314 | NGC 3100 | 0.0088 | 0.5 | 23.0 | I | 38.0 | 2629$\pm$20" (Table 1); "(3) Galaxy redshift taken from the NASA/IPAC extragalactic database (NED)." (Table 1)

## Data provenance

- ALMA projects: 2015.1.01572.S
- bands: Band 6 (~230 GHz)  
  > "We used ALMA Band 6 ($\approx$230 GHz) to observe nine of the sample members." (3 ALMA observations and data reduction)
- frequencies and spectral setup: 4 spectral windows: one on redshifted 12CO(2-1) with 1920 x 1.129 MHz channels; three continuum windows with 128 x 31.25 MHz channels  
  > "the other three, used to map the continuum emission, had 128 31.25-MHz-wide channels." (3 ALMA observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: 12-m main array, 36-43 antennas  
  > "Between 36 and 43 12-m antennas were used, with maximum baseline lengths ranging from 460 m to 1.1 km." (3 ALMA observations and data reduction)
- configurations: _not stated_
- baselines: max baselines 460 m to 1.1 km  
  > "Between 36 and 43 12-m antennas were used, with maximum baseline lengths ranging from 460 m to 1.1 km." (3 ALMA observations and data reduction)
- angular resolution: continuum beams 0.3-1 arcsec FWHM  
  > "This allowed us to obtain root-mean square (rms) noise levels ranging from 0.02 to 0.06 mJy beam$^{-1}$ for synthesized beams of 0.3 – 1 arcsec FWHM." (Continuum imaging)
- max recoverable scale: about 9.7-11.0 arcsec (1.3-6.6 kpc)  
  > "NGC 3100 | 2016-03-22     | 228.6299 (2484)     | 28.5  | 1.9, 10.6" (Table 2)
- sensitivity: continuum rms 0.02-0.06 mJy/beam; CO cube rms 0.2-1.3 mJy/beam  
  > "The cleaned CO data cubes are characterised by rms noise levels (determined in line-free channels) between 0.2 and 1.3 mJy beam$^{-1}$." (3.2 Line imaging)
- time on source: 3 to 30 minutes per target  
  > "The total time on-source ranged from 3 to 30 minutes." (3 ALMA observations and data reduction)
- observing dates: March to July 2016 (Cycle 3)  
  > "ALMA observations were taken during Cycle 3, between March and July 2016 (PI: I. Prandoni)." (3 ALMA observations and data reduction)
- pi or archival as stated: PI: I. Prandoni (Cycle 3)  
  > "(PI: I. Prandoni)" (3 ALMA observations and data reduction)
- Line: 12CO J=2-1 (230.5380 GHz)
- Other facility **VLA (archival)**: 4.9, 8.5 or 14.9 GHz continuum maps re-analysed for comparison with ALMA  
  > "All of the archival VLA datasets used in this work have been re-analysed using self-calibration and multi-scale clean as appropriate." (3.1 Continuum imaging)
- Other facility **HST / ground-based optical**: Archival optical images for dust-CO comparison  
  > "we downloaded HST images (available only for NGC 3557 and IC 4296) from the Hubble Legacy Archive" (Ancillary Data)
- Other facility **APEX**: CO(2-1) line widths for undetected sources (Paper II)  
  > "We assumed the line FWHM measured from APEX CO(2-1) observations (Paper II" (4.2 Line widths and profiles)
- External data: Mean CO(2-1)/CO(1-0) ratio R21 = 2.32 from 15 radio-loud ETGs  
  > "The mean ratio for 15 radio-loud ETGs observed in both CO transitions with the Institute de Radioastronomie Millimetrique (IRAM) 30m telescope is 2.32." (4.3 Molecular gas masses) [from (cite: Ocana10)]
- External data: HI spin temperature of 100 K and HI absorption upper limit tau<0.041 for IC 4296  
  > "If we assume an HI spin temperature of 100 K (cite: Morganti01)" (6.2.2 Absorption in IC 4296) [from (cite: Morganti01)]
- External data: Parent sample of radio galaxies from the Parkes 2.7-GHz survey  
  > "This sample was selected from (cite: Ekers89), who presented a complete sample of 91 radio galaxies from the Parkes 2.7-GHz survey" (2 The southern radio galaxy sample) [from (cite: Ekers89)]

## Processing

### Calibration

- pipeline or manual: customized Python data reduction scripts, each dataset calibrated separately  
  > "calibrating each dataset separately using customized PYTHON data reduction scripts." (3 ALMA observations and data reduction)
- casa version: CASA 4.7.2  
  > "package, version 4.7.2" (3 ALMA observations and data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan and Pallas primary; secondary standards J1037-2934, J1107-4449, J2537-5311, J0538-4405, J1427-4206  
  > "Titan and Pallas were used as primary flux calibrators" (3 ALMA observations and data reduction)
- flux scale uncertainty: 10% of S230 dominates the flux uncertainty  
  > "The uncertainties are estimated as $\sqrt{{\rm rms}^{2} + (0.1 \times S_{\rm 230})^{2}}$, and the second term dominates in all cases." (Table 3)
- self calibration: multiple cycles of phase-only self-cal for all; amplitude+phase for brightest cores only  
  > "multiple cycles of phase-only self calibration were performed in all cases. Additional amplitude and phase self-calibration was performed for the brightest cores only." (3.1 Continuum imaging)

### Imaging

- task: CLEAN in MFS mode, nterms=1 for continuum; clean for line cubes  
  > "using the CLEAN task in multi-frequency synthesis (MFS) mode with one Taylor series term" (3.1 Continuum imaging)
- deconvolver: _not stated_
- weighting robust: natural weighting for continuum and line  
  > "All the continuum maps were made using natural weighting in order to maximise the sensitivity" (3.1 Continuum imaging)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: line emission regions identified interactively; cleaned to 1.5 x rms  
  > "The continuum-subtracted dirty cubes were cleaned in regions of line emission (identified interactively) to a threshold equal to 1.5 times the rms noise level" (3.2 Line imaging)
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub, linear fit in frequency to line-free channels; for non-detections the three continuum SPWs only  
  > "using the casa task uvcontsub to form a continuum model from linear fits in frequency to line-free channels and to subtract it from the visibilities" (3.2 Line imaging)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: channel widths 10-40 km/s (75-80 km/s for non-detections)  
  > "the final channel widths range from 10 to 40 km s$^{-1}$." (3.2 Line imaging)
- final beam: 0.3-1.0 arcsec  
  > "IC 1531       | 2016-06-02     | 224.7774 (7702)     | 12.0  | 5.6, 10.9     | 0.7           | 0.6           | 87    | 360" (Table 2)
- final rms: continuum 0.02-0.06 mJy/beam  
  > "This allowed us to obtain root-mean square (rms) noise levels ranging from 0.02 to 0.06 mJy beam$^{-1}$" (3.1 Continuum imaging)

### Inherited from earlier work

- Masked moment technique for moment maps  
  > "using the masked moment technique as described by (cite: Dame11)" (4.1 CO moment maps) [from (cite: Dame11); (cite: Davis17)]
- CO mass formula and Milky Way XCO = 2e20  
  > "Following (cite: Bolatto13) and (cite: Tremblay16), we assume the average Milky Way value of $X$~CO~$=2 \times 10^{20}$ cm$^{-2}$K km s$^{-1}$." (4.3 Molecular gas masses) [from (cite: Bolatto13); (cite: Tremblay16)]
- Upper-limit relation for undetected CO  
  > "3$\sigma$ upper limits on the integrated flux densities were calculated from the relation (cite: Koay15)" (4.2 Line widths and profiles) [from (cite: Koay15)]
- Alignment angle definition and B-I dust map method  
  > "Following (cite: deKoff00) and (cite: deRuiter02), we estimated the alignment angles" (6.3 Jets and molecular gas) [from (cite: deKoff00); (cite: deRuiter02)]
- APEX CO line widths and detailed sample properties  
  > "We assumed the line FWHM measured from APEX CO(2-1) observations (Paper II" (4.2 Line widths and profiles) [from Paper II]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges per target for uvcontsub
- Image size and cell size
- Clean mask details and number of iterations
- Self-calibration solution intervals and number of cycles
- Phase center/coordinates of targets
- Flux density used for secondary calibrators and bandpass/phase calibrator per execution block
- Exact box sizes for spectral extraction (only in captions)
- uv ranges used for spectral index maps
- Primary beam correction details

## Analysis recipe

1. **Continuum imaging and core/jet photometry**: MFS imaging with natural weighting using three continuum SPWs plus line-free channels, self-calibration, 2D Gaussian fits to components  
  > "Two-dimensional Gaussian fits were performed within the regions covered by the continuum emission in order to estimate the spatial extent of each observed component." (3.1 Continuum imaging)
   - software: CASA
   - parameter: nterms=1, natural weighting  
  > "using the CLEAN task in multi-frequency synthesis (MFS) mode with one Taylor series term" (3.1 Continuum imaging)
   - fitting: _not stated_
   - validation: Compared with re-analysed archival VLA maps at matched resolution  
  > "chosen to match as closely as possible the angular resolution of the corresponding ALMA image" (3.1 Continuum imaging)
2. **Spectral indices of core and jets**: Core indices between 230 GHz and VLA frequency; spectral index maps for NGC 3100 and NGC 3557 from matched-beam, same-uv-range images with immath  
  > "The maps were restored with the same synthesized beam and spectral index maps were then produced using the casa task IMMATH." (6.1 Origin of the 230 GHz continuum emission)
   - software: CASA
   - assumption: S proportional to nu^alpha  
  > "(-0.2$<\alpha<$0.2, for $S \propto \nu^{\alpha}$)" (6.1 Origin of the 230 GHz continuum emission)
   - fitting: _not stated_
   - validation: _not stated_
3. **Line cube production and moment maps**: uvcontsub, clean with natural weighting; masked moment maps from smoothed-cube mask (1.2-2 sigma threshold) applied to unsmoothed cubes  
  > "We used thresholds varying from 1.2 to 2$\sigma$, depending on the significance of the CO detection" (4.1 CO moment maps)
   - software: CASA
   - parameter: Gaussian smoothing with beam FWHM, then Hanning smoothing in velocity  
  > "a copy of the cleaned data cube is first Gaussian-smoothed spatially (with a FWHM equal to that of the synthesised beam) and then Hanning-smoothed in velocity" (4.1 CO moment maps)
   - fitting: 2D Gaussian fits to moment 0 for CO size  
  > "The extent of the molecular gas was estimated by performing 2D Gaussian fits to the moment 0 maps" (4.1 CO moment maps)
   - validation: _not stated_
4. **Integrated spectra, line widths, upper limits**: Spectra from boxes around CO; FWZI as range of channels >=3 sigma, FWHM from channel ranges above half peak; 3 sigma upper limits for non-detections  
  > "We did not attempt to fit models to the spectra at this stage." (4.2 Line widths and profiles)
   - assumption: Upper limits assume emission within the beam; APEX line FWHM assumed  
  > "Equation [\[eq:upper_limits\]](#eq:upper_limits) is only valid if all of the molecular gas is concentrated within the synthesized beam (a few hundred parsec)." (Line widths and profiles)
   - fitting: _not stated_
   - validation: _not stated_
5. **Derive molecular gas masses**: Mmol = 1.05e4/R21 (XCO/2e20) (1/(1+z)) (S dv) D_L^2  
  > "We adopted the following relation to estimate the total molecular gas masses, including contributions from heavy elements (cite: Bolatto13)" (4.3 Molecular gas masses)
   - parameter: R21 = 2.32  
  > "We therefore take $R$~21~$=2.32$." (4.3 Molecular gas masses)
   - assumption: Milky Way XCO = 2e20 cm^-2 (K km/s)^-1  
  > "we assume the average Milky Way value of $X$~CO~$=2 \times 10^{20}$ cm$^{-2}$K km s$^{-1}$." (4.3 Molecular gas masses)
   - fitting: _not stated_
   - validation: IC 4296 flux compared with Boizelle17 ALMA Cycle 2  
  > "They reported a 5$\sigma$ CO(2-1) detection with an integrated flux of 0.76 Jy km s$^{-1}$" (5 IC 4296)
6. **CO absorption in IC 4296**: Re-image at 3 km/s channels, extract spectrum from 0.4x0.4 arcsec box at core, derive optical depth from core flux  
  > "we re-imaged the visibility data into a cube with a channel width of 3 km s$^{-1}$" (6.2.2 Absorption in IC 4296)
   - software: CASA
   - assumption: HI Tspin 100 K, CO Tex 10 K, HI/H2 ratio ~1e-2  
  > "a CO excitation temperature of 10 K (cite: Heyer09), and an HI to H~2~ column density ratio of $\sim10$^-2^" (6.2.2 Absorption in IC 4296)
   - fitting: _not stated_
   - validation: Compared to HI absorption limit of Morganti01  
  > "well below the upper limit calculated by (cite: Morganti01)" (6.2.2 Absorption in IC 4296)
7. **Jet/CO disc alignment**: |DeltaPA| = |PA_CO - PA_jet| in 0-90 deg from velocity maps and continuum/VLA jet axes  
  > "we estimated the alignment angles as $|\Delta PA|=|PA\textsubscript{CO}-PA\textsubscript{jet}|$ ranged in $0 - 90^\circ$." (6.3 Jets and molecular gas)
   - assumption: Projected angles only; no inclinations  
  > "A more comprehensive analysis would require 3D modelling of both the radio jets and the molecular gas disc" (6.3 Jets and molecular gas)
   - fitting: _not stated_
   - validation: Compared with earlier dust-jet studies  
  > "These results are statistically consistent with earlier findings based on the analysis of jets and dust lanes" (6.3 Jets and molecular gas)

## Software

- **CASA** 4.7.2: calibration, imaging (clean), uvcontsub, immath  
  > "We reduced the data using the Common Astronomy Software Application (cite: McMullin07) package, version 4.7.2" (3 ALMA observations and data reduction)
- **Python** : customized data reduction scripts  
  > "using customized PYTHON data reduction scripts." (3 ALMA observations and data reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Molecular gas mass range (detections) | 2.0e7 to 2.0e10 | not stated | Msun | 5 | The estimated molecular masses range from $2.0\times10^{7}$ to $2.0\times10^{10}$ M~$\odot$~ |
| NGC 612 molecular gas mass | 2.0e10 | 0.2e10 | Msun | 5 | NGC 612 / 760 / 840 / 273$\pm$27 / $(2.0\pm0.2)\times10^{10}$ |
| NGC 3100 molecular gas mass | 1.2e8 | 0.1e8 | Msun | 5 | NGC 3100 / 340 / 440 / 18$\pm$1.8 / $(1.2\pm0.1)\times10^{8}$ |
| CO detection S/N range | 8 to 45 | not stated | dimensionless | 3 | with S/N ranging from 8 to 45 |
| IC 4296 core 230 GHz flux density | 190 | 19.0 | mJy | 1 | core          /                   / 190$\pm$19.0  / (0.1$\times$0.1) |
| NGC 612 CO major axis extent | 9.6 | 0.3 | kpc | 3 | (9.6$\pm$0.3)$\times$(1.2$\pm$0.05) |
| IC 4296 CO absorption optical depth | 0.12 | not stated | dimensionless | 6 | the resulting optical depth is $\tau \approx 0.12$. |
| IC 4296 integrated absorption flux | 0.14 | not stated | Jy km/s | 6 | resulting in an integrated absorption flux of $\approx$0.14 Jy km s$^{-1}$ |
| Jet spectral index (NGC 3100, NGC 3557) | -0.7 | not stated | dimensionless | 2 | while the jet spectra are steeper ($\alpha \approx -0.7$) |
| Fraction of CO discs with |DeltaPA|>=60 deg | 67 (4 of 6) | 33% | percent | 7 | In four of the six detected galaxies (67$\pm33$%) we measure large misalignements ($/\Delta PA/\geq60^{\circ}$) |
| CO mass upper limits for non-detections | 1.0-6.7e6 | not stated | Msun | 5 | upper limits for the non-detections are in the range $1.0-6.7\times10^{6}$ M$_{\rm \odot}$ |

## Qualitative findings

- 230 GHz continuum cores and jets are morphologically similar to cm-wave VLA images and dominated by synchrotron emission  
  > "It is likely to be dominated by radio synchrotron emission from the core and jet structures." (6.1 Origin of the 230 GHz continuum emission)
- NGC 3100 CO ring disrupted toward the northern jet, suggesting jet/disc interaction  
  > "an interaction between the CO disc and the jets is very likely in this case." (Summary and conclusions)
- Dust and CO are co-spatial where optical imaging exists  
  > "dust absorption and CO emission trace the same ISM component, as expected." (Summary and conclusions)

## Claim tuples

- H: Is the 230 GHz continuum of LERGs dominated by synchrotron emission from jets? | E: Compared ALMA and archival VLA maps; computed core spectral indices and indices maps | R: Cores flat (-0.2<alpha<0.2), jets alpha~-0.7; morphologies match | F: Synchrotron dominates up to 230 GHz | **supported**
- H: Do LERGs host substantial molecular gas in discs? | E: 12CO(2-1) imaging of nine LERGs | R: Six of nine detected, 2e7-2e10 Msun, disc-like | F: LERGs contain molecular gas in rotating discs | **supported**
- H: Are gas discs orthogonal to jets in projection? | E: Measured |DeltaPA| for six CO detections | R: Four of six have |DeltaPA|>=60 deg; two smaller | F: Consistent with previous dust studies but small sample | **partially**
- H: Is there evidence for jet/gas interaction? | E: Examined NGC 3100 moment maps vs jets | R: Ring discontinuity toward northern jet, enhanced brightness and width | F: Possible jet/disc interaction in NGC 3100 | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Natural weighting chosen to maximise sensitivity to jet emission  
  > "All the continuum maps were made using natural weighting in order to maximise the sensitivity, with the goal of imaging emission from the jets." (3.1 Continuum imaging)
- How they decided it was enough: _not stated_
- Limitation (authors): Upper limits underestimated if CO is resolved; R21 and XCO uncertain  
  > "this assumption leads to a significant underestimation of the total flux limit." (4.2 Line widths and profiles)
- Limitation (authors): Projection effects limit alignment analysis; 3D modelling needed  
  > "A more comprehensive analysis would require 3D modelling of both the radio jets and the molecular gas disc" (6.3 Jets and molecular gas)
- Caveat (inferred, ours): Assumed Galactic XCO and R21=2.32 may be inappropriate for ETGs, affecting masses by large factors
- Caveat (inferred, ours): Small sample (six detections) limits alignment statistics
- Caveat (inferred, ours): Mixed resolution VLA data limit spectral index comparisons
- Caveat (inferred, ours): Flux scale uncertainty set at 10% without justification

## Reproducibility

- Data public (paper): ALMA data from project 2015.1.01572.S; VLA data from NRAO archive  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#\[2015.1.01572.S\]." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Line-free channel ranges
- Missing: Image/cell sizes
- Missing: Self-calibration parameters
- Missing: Exact spectrum extraction boxes
- Missing: Target coordinates
- Data volume (inferred): ~50-150 GB (nine Band 6 datasets, 1.1 GHz-resolution continuum+line cubes, raw)
- Score (inferred): 3/5, Public data and clear mass/moment recipe, but key imaging and self-cal parameters missing; mostly measurement-based results.
- Rediscovery candidate: yes, Public data, standard CASA workflow, numeric tabulated results (fluxes, masses, line widths).

## Links

- Method: (cite: Dame11); (cite: Davis17) (masked moment technique)
- Method: (cite: Bolatto13) (CO to H2 mass relation)
- Companion: Paper II (APEX CO(2-1) measurements of the sample)
- Companion: Warren et al., in preparation (VIMOS IFU spectroscopy)
- Related: 2018.1.01095.S (Cycle 6 follow-up of NGC 3100)
- Related: ATLAS3D (radio-quiet control sample)

## Checks

```json
{
 "quotes": 85,
 "quotes_ok": 85,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2018.1.01095.S"
 ],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 90,
  "stated": 65,
  "rate": 0.722
 },
 "evidence_ok": true
}
```
