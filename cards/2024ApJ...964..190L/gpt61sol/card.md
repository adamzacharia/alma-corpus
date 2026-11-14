# Mapping the Vertical Gas Structure of the Planet-hosting PDS 70 Disk

`2024ApJ...964..190L` | The Astrophysical Journal 2024 | first author: Law, Charles J. | arXiv: 2401.03018 | DOI: 10.3847/1538-4357/ad24d2

Card schema 1.0 | model gpt-6.1-sol | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry, exoplanets
- Question: Map line emitting heights, search for planetary perturbations, and constrain the disk thermal structure and CO snowline.  
  > "Using these methods for the PDS 70 disk, we can map out the line emitting heights and conduct a detailed search for vertical perturbations, such as those driven by the embedded planets PDS 70b and 70c." (Introduction); "By combining multiple optically-thick molecular lines, which trace different heights in the disk, we can also empirically derive the full two-dimensional (2D) temperature distribution" (Introduction)
- Target **PDS 70**: coordinates _not stated_; z/distance 112 pc  
  > "at a distance of 112 pc (cite: Gaia21) in the Upper Centaurus Lupus association" (Introduction); distance from (cite: Gaia21)  
  > "at a distance of 112 pc (cite: Gaia21) in the Upper Centaurus Lupus association" (Introduction)
- Target **GM Aur**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **LkCa 15**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.00888.S, 2017.A.00006.S, 2017.1.01151.S, 2018.A.00030.S, 2018.1.01230.S, 2019.1.01619.S
- bands: Band 6; Band 7  
  > "For these Band 6 data, we followed the same self-calibration procedure, in line with (cite: Andrews18; Benisty2021)." (Self Calibration and Imaging); "We obtained archival Band 7 observations of the $^{12}$CO J=3–2 and HCO$^+$ J=4–3 lines from the datasets presented in (cite: Benisty2021)" (Self Calibration and Imaging)
- frequencies and spectral setup: Three J=2–1 CO isotopologue lines in one spectral setup; 233 GHz continuum; 344 GHz literature continuum.  
  > "The three J=2–1 CO isotopologue lines are included in one spectral setup of the (cite: Facchini21PDS) program." (Self Calibration and Imaging); "The resulting 233 GHz continuum image had a flux density of 58.3 mJy within the CLEAN mask" (Self Calibration and Imaging); "and the 344 GHz continuum emission. The continuum image is taken from (cite: Isella19)." (Self Calibration and Imaging)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: Short-baseline (SB) and long-baseline (LB) data  
  > "The SB data were self-calibrated first, and then concatenated to the LB data before running a new self-calibration." (Self Calibration and Imaging)
- baselines: _not stated_
- angular resolution: Approximately 0.1 arcsec  
  > "We present observations of a suite of CO isotopologue and HCO$^+$ lines toward the PDS 70 disk at high angular resolution (${\approx}0.1\ensuremath{''}$)." (Conclusions)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: 2019.1.01619.S: S. Facchini; archival 2015.1.00888.S: E. Akiyama and 2017.A.00006.S: M. Keppler; unpublished LB 2018.A.00030.S: M. Benisty.  
  > "We present long-baseline (LB) observations associated with the ALMA program (2019.1.01619.S; PI: S. Facchini)" (Observational Details); "compiled from ALMA programs 2015.1.00888.S (PI: E. Akiyama) and 2017.A.00006.S (PI: M. Keppler), which were presented in (cite: Long_Zach18; Keppler19; Facchini21PDS)." (Observational Details); "We also include unpublished LB data of the same lines from 2018.A.00030.S (PI: M. Benisty)." (Observational Details)
- Line: 12CO J=2–1 (not stated)
- Line: 13CO J=2–1 (not stated)
- Line: C18O J=2–1 (not stated)
- Line: 12CO J=3–2 (not stated)
- Line: HCO+ J=4–3 (not stated)
- Other facility **SPHERE IRDIS**: 2016 J-band Q_phi polarimetric image for scattered-light ring height  
  > "by fitting an ellipse to the peak flux using the 2016 SPHERE IRDIS J-band, Q$_{\phi}$ polarimetric image from (cite: Keppler18)." (Comparison with NIR Scattering Surface)
- Other facility **Gaia**: PDS 70 distance of 112 pc  
  > "at a distance of 112 pc (cite: Gaia21)" (Introduction)
- External data: PDS 70 distance: 112 pc  
  > "at a distance of 112 pc (cite: Gaia21)" (Introduction) [from (cite: Gaia21)]
- External data: Planet locations: PDS 70b approximately 22 au; PDS 70c approximately 34 au  
  > "PDS 70b and 70c are located at ${\approx}$22 and ${\approx}$34 au, respectively, in a near 2:1 mean motion resonance (cite: Bae19; Wang21)." (Introduction) [from (cite: Bae19; Wang21)]
- External data: Disk PA=160.4 degrees; inclination=51.7 degrees  
  > "We first adopted a PA=160$^{\circ}$.4 and inc=51$^{\circ}$.7 for the PDS 70 disk (cite: Keppler19; Facchini21PDS)" (Emission Surface Extraction) [from (cite: Keppler19; Facchini21PDS)]
- External data: 344 GHz continuum image  
  > "and the 344 GHz continuum emission. The continuum image is taken from (cite: Isella19)." (Self Calibration and Imaging) [from (cite: Isella19)]
- External data: Power-law NIR surface and 2016 SPHERE IRDIS J-band polarimetric image  
  > "shows the power-law NIR surface derived in (cite: Keppler18) versus the extracted molecular gas heights." (Comparison with NIR Scattering Surface); "by fitting an ellipse to the peak flux using the 2016 SPHERE IRDIS J-band, Q$_{\phi}$ polarimetric image from (cite: Keppler18)." (Comparison with NIR Scattering Surface) [from (cite: Keppler18)]
- External data: Consistently derived literature CO heights versus stellar mass and disk size  
  > "versus the stellar mass and disk size compiled from consistently derived heights (cite: Law23)." (Outer Disk Vertical Structure of PDS 70 in Context) [from (cite: Law23)]
- External data: Expected height scaling relations and positive 12CO–disk-size trend  
  > "We also include several expected scaling relations, i.e., assuming line emission heights scale with gas pressure scale heights, and a previously-identified positive $^{12}$CO-R$_{^{12}\rm{CO}}$ trend (cite: Law22; Law23)." (Outer Disk Vertical Structure of PDS 70 in Context) [from (cite: Law22; Law23)]
- External data: GM Aur HCO+ J=3–2 data re-fitted for comparison  
  > "For consistency, we re-fit the HCO$^+$ J=3–2 data in the GM Aur disk from (cite: Huang20) using an exponentially-tapered power-law with the same procedure as in Section" (Outer Disk Vertical Structure of PDS 70 in Context) [from (cite: Huang20)]
- External data: LkCa 15 molecular emission surfaces  
  > "Here, we compare the PDS 70 disk to that of LkCa 15, which is one of the few transition disks whose vertical emission structure has been mapped in detail with multiple molecular lines (cite: Leemker22; Law23)." (Comparison to the LkCa 15 Transition Disk) [from (cite: Leemker22; Law23)]
- External data: CO freeze-out temperature range: 18–22 K  
  > "If we adopt a reasonable range of possible CO freeze-out temperatures from 18-22 K (cite: Collings04; Oberg05; Rafa14; Facchini17)" (CO Snowline Location) [from (cite: Collings04; Oberg05; Rafa14; Facchini17)]
- External data: Gas C/O interpretation depends on the CO2 snowline; likely C/O less than or approximately 1.0  
  > "Depending on the exact location of the CO$_2$ snowline, this gas likely has a C/O of ${\lesssim}$1.0 (cite: Oberg11)" (CO Snowline Location) [from (cite: Oberg11)]
- External data: PDS 70 photospheric C/O: 0.44 ± 0.19  
  > "Based on its photospheric abundances of carbon and oxygen, PDS 70 has a C/O ratio of 0.44 $\pm$ 0.19 (cite: Suarez18; Cridland23)." (CO Snowline Location) [from (cite: Suarez18; Cridland23)]
- Simulation/model as data: Literature scaling relations assuming line emission heights scale with gas pressure scale heights  
  > "We also include several expected scaling relations, i.e., assuming line emission heights scale with gas pressure scale heights, and a previously-identified positive $^{12}$CO-R$_{^{12}\rm{CO}}$ trend (cite: Law22; Law23)." (Outer Disk Vertical Structure of PDS 70 in Context)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: v5.8 for self-calibration; v6.2 for imaging  
  > "The self-calibration was performed with CASA `v5.8` (cite: McMullin_etal_2007; CASA)." (Self Calibration and Imaging); "We imaged the five lines discussed in this paper with CASA `v6.2`." (Self Calibration and Imaging)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: SB: four phase-only and one amplitude rounds; LB: three phase-only and one amplitude rounds. Band 7 uses gain solutions from Benisty2021 datasets.  
  > "Four rounds of phase-only and one round of amplitude self-calibration were performed on the SB data, and three rounds of phase-only and one of amplitude on the LB data, respectively." (Self Calibration and Imaging); "from the datasets presented in (cite: Benisty2021), for which we applied the same gain solutions to the line spectral windows." (Self Calibration and Imaging)

### Imaging

- task: tclean; threshold 3.5 sigma  
  > "The channel maps were restored using `tclean` with a threshold of $3.5\sigma$." (Self Calibration and Imaging)
- deconvolver: _not stated_
- weighting robust: 12CO 2–1: 0.25; 13CO 2–1 and C18O 2–1: 0.5; 12CO 3–2 and HCO+ 4–3: 1.0  
  > "| $^{12}$CO J=2–1 | 0.13 $\times$ 0.10, $-$83.7 | 0.61 | 0.25 | 0.30 | 0.93 | 209 $\pm$ 4 | P2019 |  |  |  |
| $^{13}$CO J=2–1 | 0.15 $\times$ 0.12, $-$80.0 | 0.46 | 0.5" (Table 1); "| C$^{18}$O J=2–1 | 0.16 $\times$ 0.13, $-$82.4 | 0.46 | 0.5 | 0.40 | 0.42 | 142 $\pm$ 7 | P2019 |  |  |  |
| $^{12}$CO J=3–2 | 0.07 $\times$ 0.06, 87.1 | … | 1.0" (Table 1); "| HCO$^+$ J=4–3 | 0.05 $\times$ 0.04, 69.3 | … | 1.0" (Table 1)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Keplerian channel masks; disk radius 3 arcsec; all emission assumed as elevated as 12CO  
  > "We used Keplerian masks for the channels generated from the `keplerian_mask` code" (Self Calibration and Imaging); "where we assumed the disk to be extended $3\ensuremath{''}$ in radius, and we conservatively assumed that all emission is as elevated as $^{12}$CO." (Self Calibration and Imaging)
- multiscale scales: _not stated_
- continuum subtraction: contsub; first-order polynomial; also image non-continuum-subtracted data with the same parameters  
  > "For both the Band 6 and Band 7 lines, we continuum-subtracted the data with the `contsub` task using a first-order polynomial." (Self Calibration and Imaging); "We also imaged the non-continuum-subtracted line data by adopting the same imaging parameters as the line only emission image cubes." (Self Calibration and Imaging)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: SB data concatenated to LB data before further self-calibration  
  > "The SB data were self-calibrated first, and then concatenated to the LB data before running a new self-calibration." (Self Calibration and Imaging)
- smoothing: _not stated_
- final beam: 12CO 2–1: 0.13×0.10 arcsec, −83.7 deg; 13CO 2–1: 0.15×0.12 arcsec, −80.0 deg; C18O 2–1: 0.16×0.13 arcsec, −82.4 deg; 12CO 3–2: 0.07×0.06 arcsec, 87.1 deg; HCO+ 4–3: 0.05×0.04 arcsec, 69.3 deg  
  > "| $^{12}$CO J=2–1 | 0.13 $\times$ 0.10, $-$83.7 | 0.61 | 0.25 | 0.30 | 0.93 | 209 $\pm$ 4 | P2019 |  |  |  |
| $^{13}$CO J=2–1 | 0.15 $\times$ 0.12, $-$80.0" (Table 1); "| C$^{18}$O J=2–1 | 0.16 $\times$ 0.13, $-$82.4 | 0.46 | 0.5 | 0.40 | 0.42 | 142 $\pm$ 7 | P2019 |  |  |  |
| $^{12}$CO J=3–2 | 0.07 $\times$ 0.06, 87.1" (Table 1); "| HCO$^+$ J=4–3 | 0.05 $\times$ 0.04, 69.3" (Table 1)
- final rms: 12CO 2–1: 0.93; 13CO 2–1: 0.62; C18O 2–1: 0.42; 12CO 3–2: 0.26; HCO+ 4–3: 0.31 mJy beam−1  
  > "0.13 $\times$ 0.10, $-$83.7 | 0.61 | 0.25 | 0.30 | 0.93 | 209 $\pm$ 4 | P2019 |  |  |  |
| $^{13}$CO J=2–1 | 0.15 $\times$ 0.12, $-$80.0 | 0.46 | 0.5 | 0.20 | 0.62" (Table 1); "0.16 $\times$ 0.13, $-$82.4 | 0.46 | 0.5 | 0.40 | 0.42 | 142 $\pm$ 7 | P2019 |  |  |  |
| $^{12}$CO J=3–2 | 0.07 $\times$ 0.06, 87.1 | … | 1.0 | 0.43 | 0.26" (Table 1); "| HCO$^+$ J=4–3 | 0.05 $\times$ 0.04, 69.3 | … | 1.0 | 0.43 | 0.31" (Table 1)

### Inherited from earlier work

- SB data details and spectral setup  
  > "Full details about these SB data, including the spectral set-up, are presented in (cite: Facchini21PDS)" (Observational Details) [from (cite: Facchini21PDS)]
- Details of archival and unpublished Band 7 programs  
  > "See (cite: Benisty2021) for additional details about each of these programs." (Observational Details) [from (cite: Benisty2021)]
- Band 6 self-calibration procedure  
  > "For these Band 6 data, we followed the same self-calibration procedure, in line with (cite: Andrews18; Benisty2021)." (Self Calibration and Imaging) [from (cite: Andrews18; Benisty2021)]
- Outer-ring ellipse disk center and continuum-mask geometry  
  > "The center was computed by fitting an ellipse to the outer ring (cite: Facchini21PDS)." (Self Calibration and Imaging); "where `tclean` was performed over an elliptical mask with a 1.5$''$ radius and inclination and position angle as in (cite: Facchini21PDS)." (Self Calibration and Imaging) [from (cite: Facchini21PDS)]
- Line list flagged before pseudo-continuum construction  
  > "After flagging the lines listed in (cite: Facchini21PDS) within $\pm15\,$km s$^{-1}$ from the line center" (Self Calibration and Imaging) [from (cite: Facchini21PDS)]
- Band 7 gain solutions  
  > "from the datasets presented in (cite: Benisty2021), for which we applied the same gain solutions to the line spectral windows." (Self Calibration and Imaging) [from (cite: Benisty2021)]
- JvM correction to final images  
  > "We thus applied the so-called JvM correction to the final images (cite: JvM95; Czekala21)" (Self Calibration and Imaging) [from (cite: JvM95; Czekala21)]
- Emission surface extraction methodology  
  > "which is based on the methodology originally presented in (cite: pinte18)." (Emission Surface Extraction); "We closely followed the methods outlined in (cite: Law21_MAPSIV), which we briefly summarize below." (Emission Surface Extraction) [from (cite: pinte18); (cite: Law21_MAPSIV)]
- Disk position angle and inclination  
  > "We first adopted a PA=160$^{\circ}$.4 and inc=51$^{\circ}$.7 for the PDS 70 disk (cite: Keppler19; Facchini21PDS)" (Emission Surface Extraction) [from (cite: Keppler19; Facchini21PDS)]
- Radial bins and moving averages at half-beam spacings  
  > "we also performed each of the same two types of binning (radially binned and moving averages) as in (cite: Law21_MAPSIV) with half-beam spacings." (Emission Surface Extraction) [from (cite: Law21_MAPSIV)]
- Exponentially-tapered power-law surface model, modified with an inner-cavity term  
  > "using an exponentially-tapered power law, which captures the inner flared surfaces and the plateau and turnover regions at larger radii (cite: Teague_19Natur)." (Emission Surface Extraction); "This is a similar form employed by (cite: Law21_MAPSIV) but here we include an additional term r$_{\rm{cavity}}$ to describe the inner gas cavity of the PDS 70 disk." (Emission Surface Extraction) [from (cite: Teague_19Natur); (cite: Law21_MAPSIV)]
- Local-baseline removal and fitting of vertical and temperature substructures  
  > "To quantify the significance of these features, including the cavity wall, we follow the fitting procedure outlined in (cite: Law21_MAPSIV)." (Emission Surfaces in the PDS 70 Disk); "using the same method as for the vertical substructures, i.e., via removing a local baseline (cite: Law21_MAPSIV)." (Radial Temperatures vs Peak Brightness Temperatures) [from (cite: Law21_MAPSIV)]
- Radial substructure naming convention  
  > "The location of line emission substructures are labeled according to their radial location rounded to the nearest au following standard nomenclature (cite: Huang18; Law21_MAPSIII)." (Radial Disk Chemical Substructure) [from (cite: Huang18; Law21_MAPSIII)]
- Disk size defined by radius enclosing 90% of total flux  
  > "We also computed the disk size of each emission line by determining the radius in which 90% of the total flux is contained (cite: Tripathi17; Ansdell18)." (Radial Disk Chemical Substructure) [from (cite: Tripathi17; Ansdell18)]
- Scattered-light ring ellipse-fitting approach  
  > "To do so, we followed the same approach outlined in (cite: Rich21) and described in detail in Appendix C of (cite: Law23)." (Comparison with NIR Scattering Surface) [from (cite: Rich21); Appendix C of (cite: Law23)]
- Radial and vertical gas-temperature extraction procedures  
  > "To do so, we followed the procedures of (cite: Law21_MAPSIV)." (Disk Thermal Structure) [from (cite: Law21_MAPSIV)]
- Two-layer temperature model with hyperbolic-tangent connection  
  > "Following (cite: Law21_MAPSIV), we fit a two-layer temperature model in which disk midplane and atmosphere temperature are power laws smoothly connected with a hyperbolic tangent function (cite: Dartois03; Dullemond20):" (2D Temperature Profiles) [from (cite: Law21_MAPSIV); (cite: Dartois03; Dullemond20)]
- Characteristic z/r measurement for literature comparison  
  > "following the procedure outlined in (cite: Law22), i.e., mean $z/r$ within the steeply-rising portion of the surfaces, for consistent comparison with literature values." (Outer Disk Vertical Structure of PDS 70 in Context); "Characteristic $z/r$ is computed as the mean and 16th to 84th percentile range within 80% of the r$_{\rm{cutoff}}$ as in (cite: Law22; Law23)." (Emission Surface Extraction) [from (cite: Law22; Law23)]

### Not stated but needed to reproduce (our reading)

- Initial visibility calibration procedure, pipeline version and complete calibration scripts.
- Exact EB identifiers, adopted common-center coordinates and per-EB amplitude rescaling factors.
- Self-calibration solution intervals, reference antennas, combination settings and gain-application selections.
- Exact continuum-fitting channel selections for each spectral window.
- Image cell size, image dimensions, deconvolver and primary-beam treatment.
- Stellar mass, systemic velocity, line-width settings and explicit height prescription used to generate Keplerian masks.
- Band 7 JvM residual-scaling factors and their implementation.
- Per-line disksurf iteration counts, brightness cutoffs and numerical z/r rejection limits.
- Surface-fit priors, likelihood, starting ensembles and convergence criteria.
- Local-baseline windows and substructure fitting functions.
- Radial-temperature fitting estimator, weighting and uncertainty propagation.
- 2D-temperature fit likelihood, priors, data selection and treatment of correlated surface measurements.
- Explicit roles of projects 2017.1.01151.S and 2018.1.01230.S in the analysis.

## Analysis recipe

1. **Align and self-calibrate the data**: Align EBs to an outer-ring ellipse center; construct pseudo-continuum data; rescale EB amplitudes; self-calibrate SB, then combined SB+LB; apply gains to spectral data.  
  > "We first re-aligned the data of the individual Execution Blocks (EBs) to a common disk center with the `fixvis` and `fixplanets` tasks." (Self Calibration and Imaging); "The SB data were self-calibrated first, and then concatenated to the LB data before running a new self-calibration." (Self Calibration and Imaging); "We finally applied the gain solutions to the full spectral data." (Self Calibration and Imaging)
   - software: CASA, fixvis, fixplanets, tclean
   - parameter: Flag listed lines within ±15 km s−1; average into 250 MHz channels  
  > "After flagging the lines listed in (cite: Facchini21PDS) within $\pm15\,$km s$^{-1}$ from the line center, we spectrally averaged the data into 250 MHz channels to create pseudo-continuum ms tables." (Self Calibration and Imaging)
   - parameter: Elliptical 1.5 arcsec radius mask; tclean source models; deep 1 sigma threshold before amplitude calibration  
  > "The `tclean` model was used as the source model for each step" (Self Calibration and Imaging); "where `tclean` was performed over an elliptical mask with a 1.5$''$ radius and inclination and position angle as in (cite: Facchini21PDS)." (Self Calibration and Imaging); "Before amplitude calibration, we `tcleaned` the data with a deep $1\sigma$ threshold." (Self Calibration and Imaging)
   - parameter: SB: four phase-only plus one amplitude rounds; LB: three phase-only plus one amplitude rounds  
  > "Four rounds of phase-only and one round of amplitude self-calibration were performed on the SB data, and three rounds of phase-only and one of amplitude on the LB data, respectively." (Self Calibration and Imaging)
   - parameter: 233 GHz continuum: robust=0.5; beam 0.15×0.12 arcsec, PA=−82.9 degrees  
  > "Using Briggs weighting with `robust`=0.5, the synthesized beam was $0.15\ensuremath{''}\times0.12\ensuremath{''}$ (PA=$-82.9^{\circ}$)." (Self Calibration and Imaging)
   - fitting: Fit an ellipse to the outer ring to determine the common center  
  > "The center was computed by fitting an ellipse to the outer ring (cite: Facchini21PDS)." (Self Calibration and Imaging)
   - validation: Check phase de-coherence before equalizing EB flux densities  
  > "Individual EBs were rescaled in amplitude to provide the same disk flux density, after verifying that phase de-coherence was not artificially reducing it." (Self Calibration and Imaging)
2. **Produce line cubes and integrated maps**: First-order continuum subtraction; Keplerian-masked tclean imaging of both subtracted and unsubtracted data; JvM correction; masked zeroth moments without a flux threshold.  
  > "For both the Band 6 and Band 7 lines, we continuum-subtracted the data with the `contsub` task using a first-order polynomial." (Self Calibration and Imaging); "We thus applied the so-called JvM correction to the final images (cite: JvM95; Czekala21)" (Self Calibration and Imaging); "using `bettermoments` (cite: Teague18_bettermoments) with the same Keplerian masks employed during CLEANing and with no flux threshold for pixel inclusion to ensure accurate flux recovery." (Self Calibration and Imaging)
   - software: CASA, contsub, tclean, keplerian_mask, bettermoments
   - parameter: tclean threshold: 3.5 sigma  
  > "The channel maps were restored using `tclean` with a threshold of $3.5\sigma$." (Self Calibration and Imaging)
   - parameter: 12CO 2–1: channel width 0.30 km s−1; JvM epsilon=0.61  
  > "| $^{12}$CO J=2–1 | 0.13 $\times$ 0.10, $-$83.7 | 0.61 | 0.25 | 0.30 | 0.93 | 209 $\pm$ 4 | P2019 |  |  |  |" (Table 1)
   - parameter: 13CO 2–1: channel width 0.20 km s−1; JvM epsilon=0.46  
  > "| $^{13}$CO J=2–1 | 0.15 $\times$ 0.12, $-$80.0 | 0.46 | 0.5 | 0.20 | 0.62 | 167 $\pm$ 5 | P2019 |  |  |  |" (Table 1)
   - parameter: C18O 2–1: channel width 0.40 km s−1; JvM epsilon=0.46  
  > "| C$^{18}$O J=2–1 | 0.16 $\times$ 0.13, $-$82.4 | 0.46 | 0.5 | 0.40 | 0.42 | 142 $\pm$ 7 | P2019 |  |  |  |" (Table 1)
   - parameter: 12CO 3–2 and HCO+ 4–3: channel width 0.43 km s−1  
  > "| $^{12}$CO J=3–2 | 0.07 $\times$ 0.06, 87.1 | … | 1.0 | 0.43 | 0.26" (Table 1); "| HCO$^+$ J=4–3 | 0.05 $\times$ 0.04, 69.3 | … | 1.0 | 0.43 | 0.31" (Table 1)
   - assumption: Mask radius 3 arcsec; all emission as elevated as 12CO  
  > "where we assumed the disk to be extended $3\ensuremath{''}$ in radius, and we conservatively assumed that all emission is as elevated as $^{12}$CO." (Self Calibration and Imaging)
   - fitting: First-order polynomial continuum fit  
  > "For both the Band 6 and Band 7 lines, we continuum-subtracted the data with the `contsub` task using a first-order polynomial." (Self Calibration and Imaging)
   - validation: _not stated_
3. **Extract and fit emission surfaces**: Extract per-pixel radius, height, brightness and velocity with disksurf; iteratively refine, filter and bin; fit exponentially-tapered power laws including an inner cavity.  
  > "We derived vertical emission heights from the line emission image cubes using the `disksurf` (cite: disksurf_Teague) Python code" (Emission Surface Extraction); "and then extracted a deprojected radius $r$, emission height $z$, surface brightness $I_{\nu}$, and channel velocity $v$ for each pixel associated with the emitting surface." (Emission Surface Extraction); "This is a similar form employed by (cite: Law21_MAPSIV) but here we include an additional term r$_{\rm{cavity}}$ to describe the inner gas cavity of the PDS 70 disk." (Emission Surface Extraction)
   - software: disksurf, emcee
   - parameter: One to five subsequent extraction iterations; brightness rejection at 2–3 times rms  
  > "We then employed an iterative fitting approach, which further refines the extracted surfaces using between one to five subsequent iterations depending on the line." (Emission Surface Extraction); "removed those points with low surface brightnesses (2-3$\times$rms)." (Emission Surface Extraction)
   - parameter: Radial bins and moving averages at half-beam spacings  
  > "we also performed each of the same two types of binning (radially binned and moving averages) as in (cite: Law21_MAPSIV) with half-beam spacings." (Emission Surface Extraction)
   - parameter: Characteristic z/r: mean and 16th–84th percentile range within 80% of r_cutoff  
  > "Characteristic $z/r$ is computed as the mean and 16th to 84th percentile range within 80% of the r$_{\rm{cutoff}}$ as in (cite: Law22; Law23)." (Emission Surface Extraction)
   - assumption: PA=160.4 degrees; inclination=51.7 degrees  
  > "We first adopted a PA=160$^{\circ}$.4 and inc=51$^{\circ}$.7 for the PDS 70 disk (cite: Keppler19; Facchini21PDS)" (Emission Surface Extraction)
   - assumption: Distance: 112 pc  
  > "at a distance of 112 pc (cite: Gaia21)" (Introduction)
   - fitting: emcee fits z0, phi, r_taper, r_cavity and psi; 64 walkers, 1000 burn-in steps, 500 posterior steps; medians and 16th/84th percentiles.  
  > "We used the Monte Carlo Markov Chain (MCMC) sampler implemented in `emcee` (cite: Foreman_Mackey13) to estimate the posterior probability distributions for: $z_0$, $\phi$, r$_{\rm{taper}}$, $r_{\rm{cavity}}$, and $\psi$." (Emission Surface Extraction); "Each ensemble used 64 walkers with 1000 burn-in steps and an additional 500 steps to sample the posterior distribution function." (Emission Surface Extraction); "shows the median values of the posterior distribution, with uncertainties given as the 16th and 84th percentiles" (Emission Surface Extraction)
   - validation: Visual checks at each extraction step; approximately Gaussian posteriors without significant parameter degeneracies  
  > "At each step, we visually confirmed the fidelity of the derived emission surfaces." (Emission Surface Extraction); "The posteriors were approximately Gaussian with no significant degeneracies between parameters." (Emission Surface Extraction)
4. **Measure vertical substructures**: Remove a local baseline and fit radial position, width and depth of each vertical feature.  
  > "In brief, we remove a local baseline around each vertical substructure and then fit for its radial position, width, and depth." (Emission Surfaces in the PDS 70 Disk)
   - fitting: Fitting procedure from Law21_MAPSIV  
  > "To quantify the significance of these features, including the cavity wall, we follow the fitting procedure outlined in (cite: Law21_MAPSIV)." (Emission Surfaces in the PDS 70 Disk)
   - validation: Features persist in unsubtracted cubes and without low-brightness filtering  
  > "We confirmed that each of substructures are also detected in emission surfaces extracted using the non-continuum-subtracted image cubes and with no filtering of low surface brightness points" (Emission Surfaces in the PDS 70 Disk)
5. **Measure radial morphology and disk sizes**: Deproject zeroth moments with GoFish radial_profile and fitted emission surfaces; derive azimuthal averages and radii enclosing 90% of line flux.  
  > "we computed azimuthally-averaged radial profiles using the `radial_profile` function in the `GoFish` Python package (cite: Teague19JOSS) to deproject the zeroth moment maps." (Radial Disk Chemical Substructure); "During deprojection, we incorporated the derived emission surfaces" (Radial Disk Chemical Substructure); "We also computed the disk size of each emission line by determining the radius in which 90% of the total flux is contained (cite: Tripathi17; Ansdell18)." (Radial Disk Chemical Substructure)
   - software: GoFish, radial_profile
   - parameter: 90% enclosed total flux defines disk size  
  > "Disk size (R$_{\rm{size}}$) was computed as the radius which encloses 90% of the total disk flux." (Table 1)
   - fitting: _not stated_
   - validation: Radial morphologies consistent with existing lower-resolution observations  
  > "Overall, the radial morphologies are consistent with existing lower resolution observations (cite: Long_Zach18; Facchini21PDS)" (Radial Disk Chemical Substructure)
6. **Compare gas and scattered-light heights**: Fit an ellipse to peak scattered-light ring flux in the 2016 SPHERE IRDIS image; compare with gas surfaces and the literature NIR power law.  
  > "by fitting an ellipse to the peak flux using the 2016 SPHERE IRDIS J-band, Q$_{\phi}$ polarimetric image from (cite: Keppler18)." (Comparison with NIR Scattering Surface); "shows the power-law NIR surface derived in (cite: Keppler18) versus the extracted molecular gas heights." (Comparison with NIR Scattering Surface)
   - fitting: Ellipse-fitting approach of Rich21 and Appendix C of Law23  
  > "To do so, we followed the same approach outlined in (cite: Rich21) and described in detail in Appendix C of (cite: Law23)." (Comparison with NIR Scattering Surface)
   - validation: Measured ring height agrees with the Keppler18 power-law trend  
  > "which agrees well with the overall power-law trend from (cite: Keppler18)" (Comparison with NIR Scattering Surface)
7. **Derive radial gas temperatures**: Repeat surface extraction on unsubtracted cubes; convert individual peak surface brightnesses with the full Planck function; fit radial temperature power laws and local dips.  
  > "on the non-continuum-subtracted image cubes, which ensures that we do not underestimate the line intensity along lines of sight containing strong continuum emission (cite: Boehler17)." (Disk Thermal Structure); "We then converted the peak surface brightness I$_{\nu}$ of each extracted pixel to a brightness temperature using the full Planck function and assume the resulting brightness temperature is equal to the local gas temperature." (Disk Thermal Structure); "To better characterize the radial temperature profiles, we fitted each line with a power law profile as:" (Radial Temperature Profiles)
   - software: disksurf, bettermoments
   - parameter: T=T100×(r/100 au)^(−q)  
  > "T = T_{100} \times \left(\frac{r}{\rm{100\,au}} \right)^{-q}," (Radial Temperature Profiles)
   - parameter: Fit ranges: 12CO 2–1, 72–204 au; 13CO 2–1, 75–164 au; 12CO 3–2, 70–216 au; HCO+ 4–3, 46–161 au  
  > "| $^{12}$CO J=2$-$1 | 72 | 204 | 32 $\pm$ 0.3 | 0.57 $\pm$ 0.03 | D115 |
| $^{13}$CO J=2$-$1 | 75 | 164" (Table 3); "| $^{12}$CO J=3$-$2 | 70 | 216 | 31 $\pm$ 0.2 | 0.79 $\pm$ 0.02 | D127 |
| HCO$^+$ J=4$-$3 | 46 | 161" (Table 3)
   - parameter: Use only pixels with derived emission heights  
  > "Hence, we only consider the brightness temperature of those pixels with derived emission heights." (Disk Thermal Structure)
   - parameter: Independent peak maps use bettermoments quadratic method and full Planck function  
  > "We generated all peak intensity maps with the ‘quadratic’ method of `bettermoments` using the full Planck function." (Emission Surfaces in the PDS 70 Disk)
   - assumption: 12CO, 13CO and HCO+ lines optically thick and in LTE  
  > "We extracted radial" (Disk Thermal Structure); "gas temperatures for the PDS 70 disk using $^{12}$CO, $^{13}$CO, and HCO$^+$." (Disk Thermal Structure); "We assume that all lines are optically thick and in LTE" (Disk Thermal Structure)
   - assumption: Line emission fills the beam; brightness temperature equals local gas temperature  
  > "We also assume that the line emission fills the beam due to the high angular resolution of the observations." (Disk Thermal Structure); "assume the resulting brightness temperature is equal to the local gas temperature." (Disk Thermal Structure)
   - fitting: Radial power-law fits; temperature-dip fitting uses the vertical-substructure method  
  > "To better characterize the radial temperature profiles, we fitted each line with a power law profile as:" (Radial Temperature Profiles); "To better quantify these temperature dips, we use the same method as for the vertical substructures" (Radial Temperature Profiles)
   - validation: Surface temperatures agree with independently extracted peak-intensity radial profiles; both 12CO temperature dips also appear in peak intensities  
  > "Overall, we find excellent agreement between the two curves." (Radial Temperatures vs Peak Brightness Temperatures); "We also note that the dips identified at ${\approx}$120 au in both $^{12}$CO J=2–1 and J=3–2" (Radial Temperatures vs Peak Brightness Temperatures); "are also present in the peak intensities." (Radial Temperatures vs Peak Brightness Temperatures)
8. **Fit the two-dimensional thermal structure**: Jointly fit temperatures at measured line heights with midplane and atmospheric radial power laws connected by a hyperbolic tangent.  
  > "By combining all lines with derived surfaces, which trace different heights in the disk, we can construct a 2D model of the temperature distribution." (2D Temperature Profiles); "Following (cite: Law21_MAPSIV), we fit a two-layer temperature model in which disk midplane and atmosphere temperature are power laws smoothly connected with a hyperbolic tangent function (cite: Dartois03; Dullemond20):" (2D Temperature Profiles)
   - software: emcee
   - parameter: Seven parameters: T_atm,0, q_atm, T_mid,0, q_mid, alpha, z0, beta  
  > "We used the MCMC sampler in `emcee` (cite: Foreman_Mackey13) to estimate the following seven parameters: $T_{\rm atm,0}$, $q_{\rm atm}$, $T_{\rm mid,0}$, $q_{\rm mid}$, $\alpha$, $z_0$, and $\beta$." (2D Temperature Profiles)
   - parameter: Midplane and atmosphere power laws normalized at 100 au  
  > "T_{\rm{mid}} (r) = T_{\rm{mid}, 0} \left( r / 100~\rm{au} \right)^{q_{\rm{mid}}}" (2D Temperature Profiles); "T_{\rm{atm}} (r) = T_{\rm{atm}, 0} \left( r / 100~\rm{au} \right)^{q_{\rm{atm}}}" (2D Temperature Profiles)
   - parameter: z_q(r)=z0(r/100 au)^beta; alpha sets transition height  
  > "where $z_q (r) = z_0 \left(r / 100~\rm{au} \right)^{\beta}$." (2D Temperature Profiles); "The $\alpha$ parameter defines the height at which the transition in the tanh vertical temperature profile occurs, while $\beta$ describes how the transition height varies with radius." (2D Temperature Profiles)
   - assumption: Optically thick LTE emission filling the beam  
  > "We assume that all lines are optically thick and in LTE" (Disk Thermal Structure); "We also assume that the line emission fills the beam due to the high angular resolution of the observations." (Disk Thermal Structure)
   - fitting: emcee: 256 walkers; 500 burn-in steps; 5000 posterior steps; 50th, 16th and 84th marginalized percentiles  
  > "We used 256 walkers, which take 500 steps to burn in and then an additional 5000 steps to sample the posterior distribution function." (2D Temperature Profiles); "which are given as the 50th, 16th, and 84th percentiles from the marginalized posterior distributions, respectively." (2D Temperature Profiles)
   - validation: C18O brightness beyond the cavity is generally consistent with the estimated midplane temperature, subject to its optical-depth limitation  
  > "Beyond the central cavity, the C$^{18}$O brightness temperature is generally consistent with our estimated midplane temperature" (CO Snowline Location); "As C$^{18}$O is not expected to be fully optically thick, especially at large radii, it only provides a lower limit on the gas temperature" (CO Snowline Location)
9. **Compare outer-disk heights with other disks**: Compare characteristic CO heights with literature stellar-mass and disk-size relations; re-fit GM Aur HCO+ data with the same surface procedure; compare cavity structure with LkCa 15.  
  > "versus the stellar mass and disk size compiled from consistently derived heights (cite: Law23)." (Outer Disk Vertical Structure of PDS 70 in Context); "For consistency, we re-fit the HCO$^+$ J=3–2 data in the GM Aur disk from (cite: Huang20) using an exponentially-tapered power-law with the same procedure as in Section" (Outer Disk Vertical Structure of PDS 70 in Context); "Thus, they are ideal systems to compare how line emitting heights change across their central cavities." (Comparison to the LkCa 15 Transition Disk)
   - assumption: Expected scaling relations assume line emission heights scale with gas pressure scale heights  
  > "We also include several expected scaling relations, i.e., assuming line emission heights scale with gas pressure scale heights" (Outer Disk Vertical Structure of PDS 70 in Context)
   - fitting: GM Aur: exponentially-tapered power-law surface fit using the emission-surface extraction procedure  
  > "For consistency, we re-fit the HCO$^+$ J=3–2 data in the GM Aur disk from (cite: Huang20) using an exponentially-tapered power-law with the same procedure as in Section" (Outer Disk Vertical Structure of PDS 70 in Context)
   - validation: PDS 70 appears typical against both the full literature sample and the transition-disk subsample  
  > "This is true for all disks, or if we only consider the sub-sample of transition disks." (Outer Disk Vertical Structure of PDS 70 in Context)
10. **Infer snowlines and accreted-gas composition**: Use the empirical midplane temperature and adopted freeze-out temperatures to estimate snowline radii; compare with planet locations and interpret gas C/O.  
  > "shows the midplane gas temperature as inferred from the 2D empirical fit" (CO Snowline Location); "If we adopt a reasonable range of possible CO freeze-out temperatures from 18-22 K (cite: Collings04; Oberg05; Rafa14; Facchini17), we estimate an approximate snowline radius of ${\approx}$56-85 au." (CO Snowline Location)
   - assumption: CO freeze-out: 18–22 K  
  > "If we adopt a reasonable range of possible CO freeze-out temperatures from 18-22 K (cite: Collings04; Oberg05; Rafa14; Facchini17)" (CO Snowline Location)
   - assumption: CO2 freeze-out: 42–52 K  
  > "a CO$_2$ snowline location of ${\approx}$21-26 au (assuming freeze-out temperatures of 42-52 K)" (CO Snowline Location)
   - assumption: C/O interpretation depends on the CO2 snowline, radial transport and chemical processing  
  > "Depending on the exact location of the CO$_2$ snowline, this gas likely has a C/O of ${\lesssim}$1.0 (cite: Oberg11)" (CO Snowline Location); "with the exact value depending on the details of radial transport and chemical processing (cite: Krijt18; Krijt20)." (CO Snowline Location)
   - fitting: _not stated_
   - validation: High-C/O interpretation consistent with independent molecular-layer chemistry  
  > "Overall, this is consistent with the findings of (cite: Facchini21PDS), who found that the PDS 70 molecular layer hosts a high C/O ratio" (CO Snowline Location)

## Software

- **CASA** v5.8; v6.2: Self-calibration with v5.8; line imaging with v6.2  
  > "The self-calibration was performed with CASA `v5.8` (cite: McMullin_etal_2007; CASA)." (Self Calibration and Imaging); "We imaged the five lines discussed in this paper with CASA `v6.2`." (Self Calibration and Imaging)
- **fixvis** : Realign EBs to a common disk center  
  > "We first re-aligned the data of the individual Execution Blocks (EBs) to a common disk center with the `fixvis` and `fixplanets` tasks." (Self Calibration and Imaging)
- **fixplanets** : Realign EBs to a common disk center  
  > "We first re-aligned the data of the individual Execution Blocks (EBs) to a common disk center with the `fixvis` and `fixplanets` tasks." (Self Calibration and Imaging)
- **tclean** : Self-calibration source models and line channel imaging  
  > "The `tclean` model was used as the source model for each step" (Self Calibration and Imaging); "The channel maps were restored using `tclean` with a threshold of $3.5\sigma$." (Self Calibration and Imaging)
- **contsub** : First-order polynomial continuum subtraction  
  > "For both the Band 6 and Band 7 lines, we continuum-subtracted the data with the `contsub` task using a first-order polynomial." (Self Calibration and Imaging)
- **keplerian_mask** : Generate Keplerian channel masks  
  > "We used Keplerian masks for the channels generated from the `keplerian_mask` code" (Self Calibration and Imaging)
- **bettermoments** : Zeroth moments and quadratic peak-intensity maps  
  > "We generated zeroth moment maps of line emission from the image cubes using `bettermoments`" (Self Calibration and Imaging); "We generated all peak intensity maps with the ‘quadratic’ method of `bettermoments` using the full Planck function." (Emission Surfaces in the PDS 70 Disk)
- **disksurf** : Extract vertical emission surfaces  
  > "We derived vertical emission heights from the line emission image cubes using the `disksurf` (cite: disksurf_Teague) Python code" (Emission Surface Extraction)
- **emcee** : MCMC surface and 2D-temperature fits  
  > "We used the Monte Carlo Markov Chain (MCMC) sampler implemented in `emcee`" (Emission Surface Extraction); "We used the MCMC sampler in `emcee` (cite: Foreman_Mackey13) to estimate the following seven parameters:" (2D Temperature Profiles)
- **GoFish** : Deproject zeroth moments and compute azimuthally averaged radial profiles  
  > "we computed azimuthally-averaged radial profiles using the `radial_profile` function in the `GoFish` Python package (cite: Teague19JOSS) to deproject the zeroth moment maps." (Radial Disk Chemical Substructure)
- **radial_profile** : GoFish function for deprojected radial profiles  
  > "we computed azimuthally-averaged radial profiles using the `radial_profile` function in the `GoFish` Python package (cite: Teague19JOSS) to deproject the zeroth moment maps." (Radial Disk Chemical Substructure)
- **Astropy** : _not stated_
- **cmasher** : _not stated_
- **Matplotlib** : _not stated_
- **NumPy** : _not stated_
- **scikit-image** : _not stated_
- **SciPy** : _not stated_

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 233 GHz continuum flux density within CLEAN mask | 58.3 | not stated | mJy | 1 | The resulting 233 GHz continuum image had a flux density of 58.3 mJy within the CLEAN mask |
| 12CO J=2–1 characteristic z/r | 0.32 | +0.01/-0.06 | dimensionless | 3 | $^{12}$CO J=2$-$1 & 1.80 & 0.41$^{+0.02}_{-0.02}$ & 0.51$^{+0.08}_{-0.06}$ & 0.37$^{+0.02}_{-0.03}$ & 1.27$^{+0.03}_{-0.02}$ & 5.74$^{+0.97}_{-0.84}$ & 0.32$^{+0.01}_{-0.06}$ |
| 13CO J=2–1 characteristic z/r | 0.09 | +0.04/-0.02 | dimensionless | 3 | $^{13}$CO J=2$-$1 & 1.45 & 0.41$^{+1.30}_{-0.24}$ & 1.29$^{+1.16}_{-0.87}$ & 0.28$^{+0.21}_{-0.21}$ & 0.74$^{+0.52}_{-0.37}$ & 1.61$^{+1.28}_{-0.75}$ & 0.09$^{+0.04}_{-0.02}$ |
| 12CO J=3–2 characteristic z/r | 0.32 | +0.02/-0.04 | dimensionless | 3 | $^{12}$CO J=3$-$2 & 1.90 & 0.43$^{+0.03}_{-0.05}$ & 0.63$^{+0.05}_{-0.13}$ & 0.35$^{+0.00}_{-0.02}$ & 1.34$^{+0.02}_{-0.03}$ & 5.40$^{+4.09}_{-1.80}$ & 0.32$^{+0.02}_{-0.04}$ |
| HCO+ J=4–3 characteristic z/r | 0.18 | +0.02/-0.09 | dimensionless | 3 | HCO$^+$ J=4$-$3 & 1.55 & 0.70$^{+0.20}_{-0.23}$ & 1.48$^{+0.89}_{-0.57}$ & 0.29$^{+0.11}_{-0.18}$ & 0.65$^{+0.14}_{-0.10}$ & 3.00$^{+0.91}_{-0.70}$ & 0.18$^{+0.02}_{-0.09}$ |
| 12CO J=3–2 Z42 radial position | 42 | ± 0.1 | au | 4 | / $^{12}$CO J=3$-$2 / Z42 / 42 $\pm$ 0.1 / 21 $\pm$ 4 / 6 $\pm$ 0.2 / 0.48 $\pm$ 0.07 / |
| 12CO J=3–2 Z42 width | 21 | ± 4 | au | 4 | / $^{12}$CO J=3$-$2 / Z42 / 42 $\pm$ 0.1 / 21 $\pm$ 4 / 6 $\pm$ 0.2 / 0.48 $\pm$ 0.07 / |
| 12CO J=3–2 Z42 height depression | 6 | ± 0.2 | au | 4 | / $^{12}$CO J=3$-$2 / Z42 / 42 $\pm$ 0.1 / 21 $\pm$ 4 / 6 $\pm$ 0.2 / 0.48 $\pm$ 0.07 / |
| 12CO J=3–2 Z42 fractional depth | 0.48 | ± 0.07 | dimensionless | 4 | / $^{12}$CO J=3$-$2 / Z42 / 42 $\pm$ 0.1 / 21 $\pm$ 4 / 6 $\pm$ 0.2 / 0.48 $\pm$ 0.07 / |
| 12CO J=2–1 Z119 radial position | 119 | ± 1 | au | 4 | / $^{12}$CO J=2$-$1 / Z119 / 119 $\pm$ 1 / 14 $\pm$ 7 / 2 $\pm$ 1 / 0.07 $\pm$ 0.06 / |
| 12CO J=3–2 Z113 radial position | 113 | ± 1 | au | 4 | /  / Z113 / 113 $\pm$ 1 / 25 $\pm$ 6 / 3 $\pm$ 1 / 0.10 $\pm$ 0.08 / |
| 13CO J=2–1 Z95 radial position | 95 | ± 2 | au | 4 | / $^{13}$CO J=2$-$1 / Z95 / 95 $\pm$ 2 / 20 $\pm$ 0.3 / 4 $\pm$ 1 / 0.28 $\pm$ 0.14 / |
| 12CO J=2–1 90%-flux radius | 209 | ± 4 | au | 5 | / $^{12}$CO J=2–1 / 0.13 $\times$ 0.10, $-$83.7 / 0.61 / 0.25 / 0.30 / 0.93 / 209 $\pm$ 4 / P2019 / |
| 13CO J=2–1 90%-flux radius | 167 | ± 5 | au | 5 | / $^{13}$CO J=2–1 / 0.15 $\times$ 0.12, $-$80.0 / 0.46 / 0.5 / 0.20 / 0.62 / 167 $\pm$ 5 / P2019 / |
| C18O J=2–1 90%-flux radius | 142 | ± 7 | au | 5 | / C$^{18}$O J=2–1 / 0.16 $\times$ 0.13, $-$82.4 / 0.46 / 0.5 / 0.40 / 0.42 / 142 $\pm$ 7 / P2019 / |
| 12CO J=3–2 90%-flux radius | 210 | ± 2 | au | 5 | / $^{12}$CO J=3–2 / 0.07 $\times$ 0.06, 87.1 / … / 1.0 / 0.43 / 0.26 / 210 $\pm$ 2 / P2015, P2017, P2018 / |
| HCO+ J=4–3 90%-flux radius | 165 | ± 3 | au | 5 | / HCO$^+$ J=4–3 / 0.05 $\times$ 0.04, 69.3 / … / 1.0 / 0.43 / 0.31 / 165 $\pm$ 3 / P2015, P2018 / |
| Scattered-light ring height | 4.5 | ± 0.1 | au | 6 | We derived a height of $4.5 \pm 0.1$ au at a radius of $53.7 \pm 0.1$ au |
| Scattered-light ring radius | 53.7 | ± 0.1 | au | 6 | We derived a height of $4.5 \pm 0.1$ au at a radius of $53.7 \pm 0.1$ au |
| 12CO J=2–1 T100 | 32 | ± 0.3 | K | 7 | / $^{12}$CO J=2$-$1 / 72 / 204 / 32 $\pm$ 0.3 / 0.57 $\pm$ 0.03 / D115 / |
| 12CO J=2–1 radial temperature q | 0.57 | ± 0.03 | dimensionless | 7 | / $^{12}$CO J=2$-$1 / 72 / 204 / 32 $\pm$ 0.3 / 0.57 $\pm$ 0.03 / D115 / |
| 13CO J=2–1 T100 | 18 | ± 0.5 | K | 7 | / $^{13}$CO J=2$-$1 / 75 / 164 / 18 $\pm$ 0.5 / 0.44 $\pm$ 0.10 /  / |
| 13CO J=2–1 radial temperature q | 0.44 | ± 0.10 | dimensionless | 7 | / $^{13}$CO J=2$-$1 / 75 / 164 / 18 $\pm$ 0.5 / 0.44 $\pm$ 0.10 /  / |
| 12CO J=3–2 T100 | 31 | ± 0.2 | K | 7 | / $^{12}$CO J=3$-$2 / 70 / 216 / 31 $\pm$ 0.2 / 0.79 $\pm$ 0.02 / D127 / |
| 12CO J=3–2 radial temperature q | 0.79 | ± 0.02 | dimensionless | 7 | / $^{12}$CO J=3$-$2 / 70 / 216 / 31 $\pm$ 0.2 / 0.79 $\pm$ 0.02 / D127 / |
| HCO+ J=4–3 T100 | 22 | ± 0.2 | K | 7 | / HCO$^+$ J=4$-$3 / 46 / 161 / 22 $\pm$ 0.2 / 0.43 $\pm$ 0.02 /  / |
| HCO+ J=4–3 radial temperature q | 0.43 | ± 0.02 | dimensionless | 7 | / HCO$^+$ J=4$-$3 / 46 / 161 / 22 $\pm$ 0.2 / 0.43 $\pm$ 0.02 /  / |
| 12CO J=2–1 D115 temperature-dip position | 115 | ± 0.3 | au | 7 | / $^{12}$CO J=2$-$1 / D115 / 115 $\pm$ 0.3 / 22 $\pm$ 11 / 2.8 $\pm$ 0.9 / 0.09 $\pm$ 0.003 / |
| 12CO J=2–1 D115 temperature depression | 2.8 | ± 0.9 | K | 7 | / $^{12}$CO J=2$-$1 / D115 / 115 $\pm$ 0.3 / 22 $\pm$ 11 / 2.8 $\pm$ 0.9 / 0.09 $\pm$ 0.003 / |
| 12CO J=3–2 D127 temperature-dip position | 127 | ± 1 | au | 7 | / $^{12}$CO J=3$-$2 / D127 / 127 $\pm$ 1 / 33 $\pm$ 12 / 2.1 $\pm$ 0.7 / 0.08 $\pm$ 0.01 / |
| 12CO J=3–2 D127 temperature depression | 2.1 | ± 0.7 | K | 7 | / $^{12}$CO J=3$-$2 / D127 / 127 $\pm$ 1 / 33 $\pm$ 12 / 2.1 $\pm$ 0.7 / 0.08 $\pm$ 0.01 / |
| 2D temperature model T_atm,0 | 33 | +0.2/-0.2 | K | 8 | / 33$^{+0.2}_{-0.2}$ / 16$^{+0.3}_{-0.3}$ / $-$0.95$^{+0.02}_{-0.02}$ / $-$0.01$^{+0.04}_{-0.04}$ / 13$^{+0.2}_{-0.2}$ / 2.13$^{+0.03}_{-0.03}$ / 0.14$^{+0.03}_{-0.03}$ / |
| 2D temperature model T_mid,0 | 16 | +0.3/-0.3 | K | 8 | / 33$^{+0.2}_{-0.2}$ / 16$^{+0.3}_{-0.3}$ / $-$0.95$^{+0.02}_{-0.02}$ / $-$0.01$^{+0.04}_{-0.04}$ / 13$^{+0.2}_{-0.2}$ / 2.13$^{+0.03}_{-0.03}$ / 0.14$^{+0.03}_{-0.03}$ / |
| 2D temperature model q_atm | −0.95 | +0.02/-0.02 | dimensionless | 8 | / 33$^{+0.2}_{-0.2}$ / 16$^{+0.3}_{-0.3}$ / $-$0.95$^{+0.02}_{-0.02}$ / $-$0.01$^{+0.04}_{-0.04}$ / 13$^{+0.2}_{-0.2}$ / 2.13$^{+0.03}_{-0.03}$ / 0.14$^{+0.03}_{-0.03}$ / |
| 2D temperature model q_mid | −0.01 | +0.04/-0.04 | dimensionless | 8 | / 33$^{+0.2}_{-0.2}$ / 16$^{+0.3}_{-0.3}$ / $-$0.95$^{+0.02}_{-0.02}$ / $-$0.01$^{+0.04}_{-0.04}$ / 13$^{+0.2}_{-0.2}$ / 2.13$^{+0.03}_{-0.03}$ / 0.14$^{+0.03}_{-0.03}$ / |
| 2D temperature model z0 | 13 | +0.2/-0.2 | au | 8 | / 33$^{+0.2}_{-0.2}$ / 16$^{+0.3}_{-0.3}$ / $-$0.95$^{+0.02}_{-0.02}$ / $-$0.01$^{+0.04}_{-0.04}$ / 13$^{+0.2}_{-0.2}$ / 2.13$^{+0.03}_{-0.03}$ / 0.14$^{+0.03}_{-0.03}$ / |
| 2D temperature model alpha | 2.13 | +0.03/-0.03 | dimensionless | 8 | / 33$^{+0.2}_{-0.2}$ / 16$^{+0.3}_{-0.3}$ / $-$0.95$^{+0.02}_{-0.02}$ / $-$0.01$^{+0.04}_{-0.04}$ / 13$^{+0.2}_{-0.2}$ / 2.13$^{+0.03}_{-0.03}$ / 0.14$^{+0.03}_{-0.03}$ / |
| 2D temperature model beta | 0.14 | +0.03/-0.03 | dimensionless | 8 | / 33$^{+0.2}_{-0.2}$ / 16$^{+0.3}_{-0.3}$ / $-$0.95$^{+0.02}_{-0.02}$ / $-$0.01$^{+0.04}_{-0.04}$ / 13$^{+0.2}_{-0.2}$ / 2.13$^{+0.03}_{-0.03}$ / 0.14$^{+0.03}_{-0.03}$ / |
| CO midplane snowline radius | approximately 56-85 | not stated | au | 10 | If we adopt a reasonable range of possible CO freeze-out temperatures from 18-22 K (cite: Collings04; Oberg05; Rafa14; Facchini17), we estimate an approximate snowline radius of ${\approx}$56-85 au. |
| CO2 snowline radius | approximately 21-26 | not stated | au | 10 | a CO$_2$ snowline location of ${\approx}$21-26 au (assuming freeze-out temperatures of 42-52 K) |
| Inferred C/O of gas accreted by both planets | approximately 1.0 | not stated | dimensionless | 10 | suggests they are both accreting from gas with a C/O ratio of ${\approx}$1.0. |

## Qualitative findings

- C18O originates at or near the midplane; its vertical structure is unresolved.  
  > "We do not resolve the vertical structure of the C$^{18}$O emission, which suggests that C$^{18}$O arises at, or near, the disk midplane." (Emission Surfaces in the PDS 70 Disk)
- The NIR scattering surface follows the 13CO surface.  
  > "The NIR surface is located at the same vertical height as the $^{13}$CO surface over the entire radial range of the NIR disk." (Comparison with NIR Scattering Surface)
- HCO+ is higher than 13CO inside approximately 100 au and lower outside.  
  > "At ${<}$100 au, the HCO$^+$ arises from higher altitudes than $^{13}$CO, but at ${>}$100au, HCO$^+$ is coming from lower altitudes than $^{13}$CO." (Emission Surfaces in the PDS 70 Disk)
- Outer vertical substructures are more likely related to the mm continuum edge than additional planets.  
  > "However, no evidence for kinematic deviations or additional embedded planets exists in the outer disk of PDS 70." (Outer Disk Vertical Structure of PDS 70 in Context); "Thus, it is more likely that these vertical substructures are instead related to the edge of the mm continuum disk due to, e.g., changing radiation fields at the dust edge." (Outer Disk Vertical Structure of PDS 70 in Context)

## Claim tuples

- H: Different molecular tracers resolve different vertical disk layers. | E: Extract CO isotopologue and HCO+ emission surfaces. | R: 12CO at z/r approximately 0.3; 13CO approximately 0.1; HCO+ approximately 0.2; C18O near the midplane. | F: The observations map gas from the disk atmosphere toward the midplane. | **supported**
- H: The central cavity produces a detectable change in emitting height. | E: Resolve and fit the inner 12CO J=3–2 surface. | R: A vertical dip and steep rise occur at approximately 15–45 au. | F: This is the first transition disk with the cavity-wall effect directly seen in emitting heights. | **supported**
- H: The two embedded planets substantially alter the outer disk's vertical gas structure. | E: Compare characteristic heights with literature disks of similar stellar mass and size. | R: PDS 70 heights appear typical in both the full sample and transition-disk subsample. | F: The outer disk appears largely decoupled from planet formation in the inner disk. | **refuted**
- H: The thermal structure places both planets inside the CO snowline and constrains their accreted-gas composition. | E: Fit a 2D temperature model and apply CO freeze-out temperatures of 18–22 K. | R: Estimated CO snowline approximately 56–85 au; inferred accreted-gas C/O approximately 1.0. | F: Both planets lie interior to the CO snowline and likely accrete high-C/O gas. | **partially**
- H: HCO+ and 13CO change their relative vertical ordering near the continuum edge. | E: Compare PDS 70 surfaces and re-extracted GM Aur HCO+ heights. | R: The HCO+/13CO surface crossover occurs exterior to the bulk mm continuum in both disks. | F: Changing illumination and ionizing-photon penetration may explain lower outer-disk HCO+ heights. | **partially**

## Reasoning

- Why this data: CO isotopologues are sufficiently bright and vertically extended; HCO+ has elevated emission and existing high-resolution observations.  
  > "which are sufficiently bright and vertically extended to allow for extraction of their vertical structure." (Observational Details); "We include HCO$^+$ in our analysis, due to its vertically-elevated emission and the availability of existing high-angular-resolution line data." (Observational Details)
- Why this method: Inclination permits direct height extraction; optically thick lines at different heights constrain the 2D thermal structure; unsubtracted cubes preserve temperature information.  
  > "The relative proximity and inclined orientation of the PDS 70 disk makes it possible to spatially resolve emission arising from elevated regions above and below the disk midplane" (Introduction); "By combining multiple optically-thick molecular lines, which trace different heights in the disk, we can also empirically derive the full two-dimensional (2D) temperature distribution" (Introduction); "on the non-continuum-subtracted image cubes, which ensures that we do not underestimate the line intensity along lines of sight containing strong continuum emission (cite: Boehler17)." (Disk Thermal Structure)
- Alternative: Continuum subtraction and brightness filtering do not explain the vertical substructures.  
  > "We confirmed that each of substructures are also detected in emission surfaces extracted using the non-continuum-subtracted image cubes and with no filtering of low surface brightness points" (Emission Surfaces in the PDS 70 Disk); "and thus, are not artifacts of the continuum subtraction or surface extraction process." (Emission Surfaces in the PDS 70 Disk)
- Alternative: The inability to recover inner 12CO J=2–1 heights is attributed to its larger beam rather than intrinsically different emitting heights.  
  > "This is likely due to the larger beam size of the J=2–1 observations (3 times larger in beam area) rather than an intrinsic difference in emitting heights" (Emission Surfaces in the PDS 70 Disk)
- Alternative: Temperature dips could reflect reduced gas surface density or altered heating at the continuum edge.  
  > "This temperature decrease could either be due to locally reduced gas surface density, in which the emission surface traces a deeper and thus cooler layer, or due to a change in heating or radiation properties related to the continuum edge." (Radial Temperature Profiles)
- Alternative: Missing cavity-wall structure in LkCa 15 may be an observational limitation.  
  > "However, the absence of this cavity wall effect in the LkCa 15 disk is likely an observational limitation, rather than indicating any fundamental differences in inner disk structure." (Comparison to the LkCa 15 Transition Disk)
- Alternative: The approximately 50 au peak-intensity dip may be a real gap rather than only continuum absorption.  
  > "However, given its appearance in the peak intensity profile, which should be less affected by continuum absorption, this suggests that it is a real feature and may hint at a true gas and dust gap." (Radial Temperatures vs Peak Brightness Temperatures)
- How they decided it was enough: Choose imaging parameters for surface extraction; visually check extraction at each step.  
  > "Overall, the ability to extract line emitting heights depends on having sufficiently high angular resolution, spectral resolution, and line sensitivities." (Self Calibration and Imaging); "Considering this, we selected the imaging parameters that best suited surface extraction for this work." (Self Calibration and Imaging); "At each step, we visually confirmed the fidelity of the derived emission surfaces." (Emission Surface Extraction)
- Limitation (authors): No direct midplane-temperature tracer interior to 100 au; fitted midplane temperatures are extrapolated.  
  > "the midplane temperature from this fit is an extrapolation from higher disk heights since we lack lines that directly trace the disk midplane interior to a radius of 100 au." (CO Snowline Location)
- Limitation (authors): Inner CO lines may become optically thin and cease tracing true gas temperatures.  
  > "the lines are likely no longer optically thick and thus do not trace the true gas temperature." (Radial Temperature Profiles)
- Limitation (authors): C18O brightness is only a lower limit on gas temperature.  
  > "As C$^{18}$O is not expected to be fully optically thick, especially at large radii, it only provides a lower limit on the gas temperature" (CO Snowline Location)
- Limitation (authors): Central-cavity heights are measurable only in 12CO J=3–2.  
  > "For all other lines besides $^{12}$CO J=3–2, no estimates of vertical heights within the central cavity were possible due to insufficient angular resolution or intrinsically flat emitting heights likely due to the low gas surface densities." (Local Perturbations and Cavity Wall)
- Limitation (authors): Literature comparison disks may themselves contain planets.  
  > "However, we note the caveat that many of the literature disks used as the comparison sample also have indirect evidence for the presence of embedded planets." (Outer Disk Vertical Structure of PDS 70 in Context)
- Limitation (authors): Only two sources support the detailed HCO+ comparison.  
  > "Although intriguing, with only two sources, it is difficult to make any additional conclusions about the vertical distribution of HCO$^+$ in protoplanetary disks more generally." (Outer Disk Vertical Structure of PDS 70 in Context)
- Limitation (authors): JvM correction can underestimate effective rms.  
  > "The effective rms, which can be underestimated when applying the JvM correction (cite: Casassus22), is not relevant for the analysis of this paper." (Self Calibration and Imaging)
- Limitation (authors): Inner CO2 snowline and C/O estimates extrapolate into a cavity without direct temperatures.  
  > "with the caveat that these are extrapolations to radii within the inner cavity where we lack direct temperature measurements." (CO Snowline Location)
- Caveat (inferred, ours): Separate measured emitting-layer temperatures from model-dependent midplane temperatures and chemical interpretations.
- Caveat (inferred, ours): Formal posterior intervals may not capture optical-depth, beam-filling, calibration and residual-scaling systematics.
- Caveat (inferred, ours): Quantify effects of correlated pixels, radial bins and subjective extraction filtering on fitted uncertainties.
- Caveat (inferred, ours): Typical outer-disk heights do not establish absence of planetary effects without a planet-free comparison sample.

## Reproducibility

- Data public (paper): Band 7 observations described as archival; some LB data described as unpublished.  
  > "We obtained archival Band 7 observations of the $^{12}$CO J=3–2 and HCO$^+$ J=4–3 lines from the datasets presented in (cite: Benisty2021)" (Self Calibration and Imaging); "We also include unpublished LB data of the same lines from 2018.A.00030.S (PI: M. Benisty)." (Observational Details)
- Products in archive: _not stated_
- Missing: Executable calibration, imaging, extraction and fitting scripts with pinned dependencies.
- Missing: Referenced SB spectral setup, Band 7 processing and gain solutions from earlier papers.
- Missing: Complete EB-to-product mapping, especially for acknowledgement-only project codes.
- Missing: Exact masks, continuum channels, self-calibration settings and amplitude rescaling factors.
- Missing: Per-line extraction selections and surface-fit likelihoods and priors.
- Missing: Temperature-fit selection, likelihood, priors and systematic uncertainty treatment.
- Missing: Machine-readable extracted surfaces and analyzed image cubes with specified access locations.
- Missing: Confirmation of public availability of every required dataset.
- Data volume (inferred): Cannot estimate reliably: visibility sizes, channel counts and image dimensions are not given.
- Score (inferred): 6/5, 6/10: project codes, named tools, image properties, model forms and sampler lengths are supplied, but calibration and extraction choices depend on earlier papers and several fit settings are missing.
- Rediscovery candidate: no, Main results are numeric and some observations are archival, but the supplied text does not establish public access to all required data or provide a complete executable recipe.

## Links

- Method: (cite: Andrews18; Benisty2021) (Inherited self-calibration procedure.)
- Method: (cite: Facchini21PDS) (SB spectral setup, line flagging, disk center and geometry.)
- Method: (cite: JvM95; Czekala21) (Residual scaling for non-Gaussian beams.)
- Method: (cite: pinte18) (Geometric emission-surface extraction methodology.)
- Method: (cite: disksurf_Teague) (Emission-surface extraction software.)
- Method: (cite: Law21_MAPSIV) (Extraction, binning, substructure fitting and thermal-structure procedures.)
- Method: (cite: Teague_19Natur) (Exponentially-tapered surface model.)
- Method: (cite: Foreman_Mackey13) (emcee posterior sampling.)
- Method: (cite: rich_teague_2020_4321137) (Keplerian imaging masks.)
- Method: (cite: Teague18_bettermoments) (Moment and peak-intensity maps.)
- Method: (cite: Teague19JOSS) (GoFish radial profiles.)
- Method: (cite: Rich21); Appendix C of (cite: Law23) (Scattered-light ring height measurement.)
- Method: (cite: Dartois03; Dullemond20) (Two-layer temperature prescription.)
- Method: (cite: Law22; Law23) (Characteristic emission heights and comparison relations.)
- Method: (cite: Tripathi17; Ansdell18) (Enclosed-flux disk sizes.)
- Companion: (cite: Facchini21PDS) (Chemical inventory and SB observations of the same program.)
- Companion: (cite: Benisty2021) (Band 7 datasets, program details and inherited gain solutions.)
- Companion: (cite: Long_Zach18; Keppler19; Facchini21PDS) (Earlier presentations of the archival PDS 70 line observations.)
- Related: exoALMA Large Program
- Related: MAPS

## Checks

```json
{
 "quotes": 273,
 "quotes_ok": 273,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 6,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2017.1.01151.S"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 41,
 "numeric_problems": 0,
 "fill": {
  "facts": 176,
  "stated": 139,
  "rate": 0.79
 },
 "evidence_ok": true
}
```
