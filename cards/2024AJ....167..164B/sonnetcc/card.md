# An ALMA Molecular Inventory of Warm Herbig Ae Disks. I. Molecular Rings, Asymmetries, and Complexity in the HD 100546 Disk

`2024AJ....167..164B` | The Astronomical Journal 2024 | first author: Booth, Alice S. | arXiv: 2402.04001 | DOI: 10.3847/1538-3881/ad2700

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: What is the molecular inventory of the HD 100546 disk, how do the molecular rings and asymmetries relate to the millimetre dust sub-structure, and how does its chemistry compare with other Herbig Ae disks  
  > "With this molecular inventory we determine the relationship (if any) between the different molecular tracers and the millimetre dust sub-structures" (Introduction); "We also investigate how similar and/or different the molecular make up of this disk is to other chemically well-characterised Herbig Ae disks." (abstract)
- Target **HD 100546**: coordinates _not stated_; z/distance 110 pc (Table 1)  
  > "HD 100546 is nearby young Herbig Ae star host to a gas-rich protoplanetary disk" (Target); "110 \[2\]" (Table 1); distance from _not stated_

## Data provenance

- ALMA projects: 2021.1.00738.S
- bands: Band 7 (about 337 to 357 GHz)  
  > "This paper presents ALMA Band 7 observations of the planet-forming disk HD 100546" (Introduction)
- frequencies and spectral setup: Two spectral settings (A and B), four spectral windows each, 976.6 kHz channels (0.84 km/s at 350 GHz), 1.875 GHz bandwidth per window; centres 338.790824, 340.732413, 348.916936, 350.775389 GHz (A) and 344.240980, 3459.40999 [sic], 354.367095, 356.067114 GHz (B)  
  > "The data consist of two spectral settings with four spectral windows each at a spectral resolution of 976.6 kHz (0.84 km s$^{-1}$ at 350 GHz) and a bandwidth of 1.875 GHz." (Data reduction); "These spectral windows are centered at 338.790824, 340.732413, 348.916936 and 350.775389 GHz for setting A and, 344.240980, 3459.40999, 354.367095 and 356.067114 GHz for setting B." (Data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C4  
  > "These observations were taken in configuration C4 in Band 7" (Data reduction)
- baselines: about 15 to about 1300 m (Table A3: 14.9-1301.6 m across execution blocks)  
  > "with baselines ranging from $\approx$15 to $\approx$1300 m" (Data reduction)
- angular resolution: about 0.3 arcsec (about 30 au); synthesized beams 0.34-0.48 x 0.23-0.39 arcsec depending on line and robust  
  > "where we target $>$20 molecules at $\approx$0.3$''$ ($\approx$30 au) resolution" (Introduction)
- max recoverable scale: MRS 2.8 to 3.9 arcsec across execution blocks (Table A3)  
  > "MRS" (Table 1)
- sensitivity: per-line rms about 0.67-0.97 mJy/beam at 0.9 km/s channels (Table of image properties)  
  > "The resulting beam sizes and rms noise for each line imaged are listed in Table" (Imaging)
- time on source: 62 min per execution block for setting A (4 blocks), 53 min per block for setting B (5 blocks)  
  > "On Source Time" (Table 1)
- observing dates: 05-01-2022 to 14-07-2022 (nine execution blocks, dd-mm-yyyy)  
  > "05-01-2022" (Table 1); "14-07-2022" (Table 1)
- pi or archival as stated: Program 2021.1.00738.S, PI A. S. Booth (same program also targeted IRS 48)  
  > "HD 100546 was observed with ALMA in program 2021.1.00738.S (PI. A. S. Booth)." (Data reduction); "This program also targeted the IRS 48 disk" (Data reduction)
- Line: CN J=7/2-5/2, F=7/2-5/2 (also N=4-3 hyperfine group imaged) (340.2477700 GHz)
- Line: SO J=7_8-6_7 (340.7141550 GHz)
- External data: Isotope ratios assumed for column densities (two ratios, 557 and 3.6, species names lost in text)  
  > "assuming /=557 and /=3.6 (cite: 1999RPPh...62..143W)" (Column densities) [from Wilson 1999 (cite: 1999RPPh...62..143W)]
- External data: Local ISM isotope ratio of 22 used to correct CS/SO isotopologue column densities  
  > "where in the local ISM / is 22 (cite: 1999RPPh...62..143W)" (Column densities) [from Wilson 1999 (cite: 1999RPPh...62..143W)]
- External data: Comparison column density profiles for HD 163296 and MWC 480 taken from MAPS papers (ion and CO from Aikawa/Zhang; HCN and CN from Bergner)  
  > "where the data for the other two disks are taken from (cite: 2021ApJS..257...13A)" (Ionization); "The resulting HCN and CN column density profiles from (cite: 2021ApJS..257...11B) are shown in Figure" (UV field) [from (cite: 2021ApJS..257...13A); (cite: 2021ApJS..257...11B); (cite: 2021ApJS..257....5Z)]
- External data: High-resolution continuum image of the dust shown alongside SO and CS maps  
  > "shows the integrated intensity maps of the dust emission from (cite: 2019ApJ...871...48P)" (Sub-structures in the HD 100546 disk) [from Pineda et al. 2019 (cite: 2019ApJ...871...48P)]
- External data: Emitting height Z/R of about 0.25 at 200 au derived by other work for comparison  
  > "both (cite: 2022ApJ...932..114L) and (cite: 2023A&A...669A.158S) derive a Z/R of $\approx$0.25 at 200 au" (Sub-structures in the HD 100546 disk) [from (cite: 2022ApJ...932..114L); (cite: 2023A&A...669A.158S)]
- Simulation/model as data: Keplerian model (outer radius 300 au) used as matched filter and Keplerian masks for CLEAN built from the disk properties in Table 1  
  > "using a Keplerian model with an outer radius of 300 au" (Line identification); "These masks were generated with the code from (cite: rich_teague_2020_4321137)." (Imaging)

## Processing

### Calibration

- pipeline or manual: standard ALMA pipeline  
  > "The data were calibrated via the standard ALMA pipeline using `CASA` version 6.2.1 (cite: 2007ASPC..376..127M)." (Data reduction)
- casa version: CASA 6.2.1  
  > "The data were calibrated via the standard ALMA pipeline using `CASA` version 6.2.1 (cite: 2007ASPC..376..127M)." (Data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J142-4206 (flux/bandpass calibrator column, as printed)  
  > "J142-4206" (Table 1)
- flux scale uncertainty: _not stated_
- self calibration: Continuum self-cal after flagging strong lines: 6 rounds of phase with decreasing solint, 1 round of amplitude, until continuum S/N plateaued (peak S/N about 525 to about 5450); solutions applied to line data  
  > "Both phase (6 rounds of decreasing solint intervals) and amplitude (1 round) calibrations were applied until the signal-to-noise of the continuum data plateaued." (Data reduction); "For HD 100546 this resulted in a peak continuum signal-to-noise increase from $\approx$525 to $\approx$5450." (Data reduction); "These solutions were then applied to the line data." (Data reduction)

### Imaging

- task: CASA tclean (written tCLEAN)  
  > "The data were imaged in CASA using `tCLEAN` with the multiscale deconvolver." (Imaging)
- deconvolver: multiscale  
  > "The data were imaged in CASA using `tCLEAN` with the multiscale deconvolver." (Imaging)
- weighting robust: Briggs robust +0.5 for strong lines; +0.5 or +2.0 for weaker lines depending on compact or extended emission  
  > "For the strong lines, a briggs robust of +0.5 was used and for the weaker lines +0.5 or +2.0 was used depending on the emission morphology" (Imaging)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Keplerian masks, cleaned to 4x the noise level of the dirty image  
  > "Individual lines were cleaned with Keplerian masks down to 4$\times$ the noise level of the dirty image." (Imaging)
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub, fit order 1  
  > "The continuum was subtracted using `uvcontsub` with a fit order of 1" (Data reduction)
- line free channels: Channels of bright lines and atmospheric absorption features excluded, chosen by visual inspection in plotms (ranges not given)  
  > "excluding channels of bright lines and atmospheric absorption features that were identified via visual inspection of the data with the `plotms` task" (Data reduction)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: All spectral windows imaged at 0.9 km/s velocity resolution  
  > "all of the spectral windows were imaged using a velocity resolution of 0.9 km s$^{-1}$" (Imaging)
- final beam: Per-line beams listed in appendix table; about 0.34-0.48 x 0.23-0.39 arcsec  
  > "The resulting beam sizes and rms noise for each line imaged are listed in Table" (Imaging)
- final rms: Per-line rms listed in appendix table; about 0.67-0.97 mJy/beam  
  > "The resulting beam sizes and rms noise for each line imaged are listed in Table" (Imaging)

### Inherited from earlier work

- Matched filtering technique for line detection  
  > "we applied matched filtering (cite: Loomis2018)" (Line identification) [from (cite: Loomis2018)]
- Column density method (LTE, optical depth correction)  
  > "We estimate column densities following the methods outlined in (cite: 2018ApJ...859..131L)." (Column density calculations) [from (cite: 2018ApJ...859..131L)]
- Keplerian mask generation code  
  > "These masks were generated with the code from (cite: rich_teague_2020_4321137)." (Imaging) [from (cite: rich_teague_2020_4321137)]
- Spectral stacking of radial annuli with GoFish  
  > "spectral stacking with *GoFish* ((cite: Loomis2018) and (cite: GoFish), respectively)" (Weak-line detections) [from (cite: GoFish)]
- Details of the IRS 48 observations from the same program deferred to Paper II  
  > "This program also targeted the IRS 48 disk and these data will be presented in (cite: Booth2023_irs48)." (Data reduction) [from (cite: Booth2023_irs48)]

### Not stated but needed to reproduce (our reading)

- Self-calibration solution intervals per round, reference antenna and solution combine/spw-map settings
- Exact line-free channel ranges used in uvcontsub
- Image size and cell size for tclean; multiscale scales; per-line clean thresholds beyond 4x dirty-image noise
- Keplerian mask parameters (outer radius, linewidth, inclination handling) beyond Table 1 values
- How the nine execution blocks were weighted and combined and whether any was down-weighted
- Source and catalogue (CDMS/JPL/other) of the Molecular Data rest frequencies, Eup, Aul, partition functions
- How ring peak radii and their uncertainties were measured, and how column density errors were propagated
- Deprojection geometry and radial bin size for profiles and polar maps
- Matched-filter implementation details (software, image filters used, noise estimation)
- Systematic flux calibration uncertainty and the calibrator flux values
- Species names for many Table entries are missing from the text, so the ratio tables cannot be mapped to molecules without the original

## Analysis recipe

1. **Calibrate, align and self-calibrate the execution blocks**: Standard ALMA pipeline calibration in CASA, alignment of blocks to a common phase centre, continuum self-calibration with strong lines flagged, applied to line data  
  > "These individually calibrated executions were aligned to a common phase centre using the `fixvis` and `fixplanets` tasks." (Data reduction); "Self-calibration was performed on the continuum data after flagging the strong lines." (Data reduction)
   - software: CASA 6.2.1, fixvis, fixplanets
   - parameter: 6 phase rounds with decreasing solint, 1 amplitude round, iterated until S/N plateau  
  > "Both phase (6 rounds of decreasing solint intervals) and amplitude (1 round) calibrations were applied until the signal-to-noise of the continuum data plateaued." (Data reduction)
   - fitting: _not stated_
   - validation: Continuum peak S/N rose from about 525 to about 5450; needed to detect the weak outer ring  
  > "Self-calibration was necessary to detect the weak outer ring of millimetre emission in the HD 100546 disk." (Data reduction)
2. **Subtract continuum and image the lines**: uvcontsub then tclean with multiscale deconvolver and Keplerian masks, 0.9 km/s channels, Briggs robust +0.5 or +2.0  
  > "The data were imaged in CASA using `tCLEAN` with the multiscale deconvolver." (Imaging); "Individual lines were cleaned with Keplerian masks down to 4$\times$ the noise level of the dirty image." (Imaging)
   - software: CASA tclean, uvcontsub, plotms, keplerian_mask
   - parameter: uvcontsub fit order 1  
  > "The continuum was subtracted using `uvcontsub` with a fit order of 1" (Data reduction)
   - parameter: velocity resolution 0.9 km/s for all windows  
  > "all of the spectral windows were imaged using a velocity resolution of 0.9 km s$^{-1}$" (Imaging)
   - fitting: _not stated_
   - validation: _not stated_
3. **Search for lines with matched filtering**: Cross-correlate a Keplerian model filter (300 au outer radius) with visibilities; detection threshold 4 sigma  
  > "This technique utilises the predictable kinematic pattern of Keplerian line emission to detect weak line emission" (Line identification); "We take a line detection to be any peak above the 4 $\sigma$ level." (Line identification)
   - software: matched filtering (Loomis et al. 2018)
   - parameter: Keplerian filter outer radius 300 au  
  > "using a Keplerian model with an outer radius of 300 au" (Line identification)
   - assumption: Filter shape must represent the emission; different filters give different S/N  
  > "As the impulse response depends on how accurately the filter represents the underlying emission structure" (Line identification)
   - fitting: _not stated_
   - validation: Different filters (Keplerian models of different sizes, image filters of strong lines) compared  
  > "different filters, e.g., Keplerian models of different sizes and image filters of different strong lines, will yield a different signal-to-noise for a detected line" (Line identification)
4. **Confirm weak lines with line-specific filters and stacking**: Matched filtering with strong lines as filters plus image-plane spectral stacking over radial regions with GoFish; annulus 180-250 au for outer-ring confirmation  
  > "we also use specific strong lines as filters to look for weaker lines of molecules that are either isotopologues of the strong line or are expected to share a common emission morphology" (Weak-line detections); "we use GoFish (cite: GoFish) to create average spectra stacked within an annulus, of 180-250 au, which encompasses the emission detected in the outer ring" (Sub-structures in the HD 100546 disk)
   - software: GoFish, matched filtering
   - parameter: annulus 180-250 au  
  > "stacked within an annulus, of 180-250 au" (Sub-structures in the HD 100546 disk)
   - fitting: _not stated_
   - validation: Cross-checked matched filter and image-plane detections (e.g. CS filter 9 sigma versus 6 sigma with Keplerian filter)  
  > "Using CS as a filter we detect with a 9 $\sigma$ significance compared to the 6 $\sigma$ with the smooth 300 au Keplerian filter." (Weak-line detections / non-detections)
5. **Make moment maps, radial profiles and locate ring peaks**: Integrated intensity maps from Keplerian-masked CLEAN cubes without clipping; azimuthally averaged radial profiles; ring-peak radii overplotted on the continuum radial profile  
  > "These line maps were generated using the Keplerian masks from the CLEAN-ing with no clipping thresholds." (Integrated intensity maps); "we plot the location of the ring peaks for each molecule in Figure" (Sub-structures in the HD 100546 disk)
   - fitting: _not stated_
   - validation: _not stated_
6. **Test emitting height of the rings**: Overlay Z/R = 0, 0.1, 0.25 ellipses at each species' peak radius on integrated intensity maps and compare ring geometry  
  > "The ellipses are tracing the Z/R (geometric height from the midplane divided by radius) of 0 (the midplane), 0.1 and 0.25 surfaces at the radius where each of the species peaks in emission." (Sub-structures in the HD 100546 disk)
   - parameter: Z/R surfaces 0, 0.1, 0.25  
  > "of 0 (the midplane), 0.1 and 0.25 surfaces" (Sub-structures in the HD 100546 disk)
   - assumption: Disk geometry from Table 1 properties  
  > "The Keplerian masks were constructed using the properties for the HD 100546 disk as listed in Table" (Imaging)
   - fitting: _not stated_
   - validation: Compared with literature emitting heights (Z/R about 0.25 at 200 au)  
  > "derive a Z/R of $\approx$0.25 at 200 au" (Sub-structures in the HD 100546 disk)
7. **Characterise azimuthal asymmetries**: Polar deprojections of integrated intensity maps for continuum and lines compared with the dust asymmetry  
  > "we show polar deprojections of the integrated intensity maps for the 0.9 mm continuum" (Sub-structures in the HD 100546 disk)
   - fitting: _not stated_
   - validation: _not stated_
8. **Derive column densities and ratios**: LTE column densities from radial profiles following Loomis et al. 2018a, over fixed excitation temperatures 30, 50, 100 K, with optical depth correction  
  > "This assumes that the gas is in local thermodynamic equilibrium and includes an optical depth correction factor where we assume a line width of 1 km s$^{-1}$." (Column density calculations); "We explore a range of excitation temperatures: 30, 50, and 100 K" (Column densities)
   - parameter: One representative transition per molecule, fixed Tex  
  > "Since we only have one detected transition for most molecules we do this over a set of fixed rotational temperatures." (Column density calculations)
   - assumption: LTE; line width 1 km/s for the optical depth correction  
  > "This assumes that the gas is in local thermodynamic equilibrium" (Column density calculations)
   - assumption: Local ISM isotope ratio of 22 for S isotopologues  
  > "where in the local ISM / is 22 (cite: 1999RPPh...62..143W)" (Column densities)
   - fitting: _not stated_
   - validation: Optical depth assessed from isotopologue ratios; inner-disk ratios flagged as tentative for possible optically thick emission  
  > "For the inner disk these column density ratios are tentative due to potentially optically thick emission." (Column densities)
9. **Compare with HD 163296, MWC 480 and other Herbig disks**: Compare column density profiles and ratios with MAPS values and HD 142527/HD 169142 literature  
  > "We will therefore mainly focus on the above individual disks where column densities have been calculated and the observations are spatially resolved." (In context with other Herbig Ae disks)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 6.2.1: Pipeline calibration, fixvis/fixplanets alignment, uvcontsub, plotms, tclean imaging  
  > "The data were calibrated via the standard ALMA pipeline using `CASA` version 6.2.1 (cite: 2007ASPC..376..127M)." (Data reduction); "The data were imaged in CASA using `tCLEAN` with the multiscale deconvolver." (Imaging)
- **keplerian_mask** 1.0: Generating Keplerian masks for CLEAN  
  > "These masks were generated with the code from (cite: rich_teague_2020_4321137)." (Imaging); "richteague/keplerian_mask: Initial Release, 1.0, Zenodo" (References)
- **GoFish** : Spectral stacking of annuli to confirm weak lines and rings  
  > "spectral stacking with *GoFish* ((cite: Loomis2018) and (cite: GoFish), respectively)" (Weak-line detections)
- **Astropy** : Additional package listed in acknowledgements, specific use not stated  
  > "This work has used the following additional software packages that have not been referred to in the main text: Astropy, IPython, Jupyter, Matplotlib and NumPy" (Acknowledgements)
- **Matplotlib** : Additional package listed in acknowledgements, specific use not stated  
  > "This work has used the following additional software packages that have not been referred to in the main text: Astropy, IPython, Jupyter, Matplotlib and NumPy" (Acknowledgements)
- **NumPy** : Additional package listed in acknowledgements, specific use not stated  
  > "This work has used the following additional software packages that have not been referred to in the main text: Astropy, IPython, Jupyter, Matplotlib and NumPy" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of molecules detected | 19 | not stated | dimensionless | 4 | In total, we have detected 19 different molecules in the HD 100546 disk. |
| Continuum peak S/N before and after self-calibration | about 525 to about 5450 | not stated | dimensionless | 1 | For HD 100546 this resulted in a peak continuum signal-to-noise increase from $\approx$525 to $\approx$5450. |
| Radius of molecular rings in outer disk | about 200 to 240 au | not stated | au | 5 | The array of molecular rings at $\approx$200 to 240 au clearly align with the location of the outer dust ring |
| Size of the gas disk traced by the CO isotopologue named in the text | 600 au (about 2x the millimetre continuum extent) | not stated | au | 5 | The gas disk traced by is 600 au in size which is $\approx$2$\times$ the radial extent of the millimetre continuum emission. |
| Emitting layer of outer molecular rings | Z/R < 0.1 | not stated | dimensionless | 6 | we can constrain this to be from a layer with Z/R$<$0.1 |
| Peak abundance ratio of two organics in the inner disk at 100 K (species names missing in text) | 18 | 4 | dimensionless | 8 | The peak column density ratios in the inner disk for / is $18\pm4$ and for / is 0.7$\pm$0.2 at 100 K for the inner disk. |
| Ion-to-CO column density ratio at about 200 au (species name missing in text) | 3-5e-7 | not stated | dimensionless | 8 | this is at least an order of magnitude lower - $3-5\times10^{-7}$ (see Table 2) |
| N(CN)/N(HCN) range across disk, 10 to 350 au | 0.1 to 10 | not stated | dimensionless | 8 | Overall we find that N(CN)/N(HCN) over the HD 100546 disk ranges from $10^{-1}$ to 10 from 10 to 350 au |
| N(CN)/N(NO) range across disk | 0.1 to 1 | not stated | dimensionless | 8 | Across the HD 100546 disk the N(CN)/N(NO) varies from $10^{-1}$ to 1. |
| CO column density at second dust ring relative to HD 163296 and MWC 480 | about 3x higher | not stated | dimensionless | 9 | the CO column density is $\approx3\times$ higher in HD 100546 compared to the other two disks at the same radii |
| SO column density in outer disk | about 3e12 | not stated | cm^-2 | 8 | The weak SO emission in the outer disk of HD 100546 has a column density of $\approx3\times10^{12}$ cm$^{-2}$ |
| Peak SO column density relative to MAPS upper limit (<3e12 cm^-2) | about 100x higher | not stated | dimensionless | 9 | Our SO peak column density in HD 100546 is $\approx100\times$ higher than the disk-averaged upper-limit in the MAPS Herbig disks of $<3\times10^{12}$ cm$^{-2}$. |
| OCS column density upper limit at 100 K | <1e12 | not stated | cm^-2 | 8 | OCS is not detected in our data and we place an upper-limit on the column density of $<$10$^{12}$ cm$\mathrm{^{-2}}$ at 100 K |
| Gas cavity size | about 15 au | not stated | au | 5 | the $\approx$15 au gas cavity in HD 100546 |

## Qualitative findings

- Molecular rings in the outer disk all peak just beyond the outer millimetre dust ring at about 200 au, linking the large dust distribution to the chemistry  
  > "Multiple molecular species are detected in rings, which are, surprisingly, all peaking just beyond the underlying millimeter continuum ring at $\approx$200 au." (abstract)
- Outer-ring brightness asymmetry is shared across molecules and follows the dust asymmetry  
  > "it is clear that the molecules peak in similar azimuthal regions of the disk and this also follows an underlying asymmetry in the dust emission" (Sub-structures in the HD 100546 disk)
- SO is centrally concentrated inside a broadly symmetric CS ring with an SO asymmetry in the warmest line  
  > "From this image gallery it is clear that the SO is sitting inside a broadly symmetric ring of CS" (Sub-structures in the HD 100546 disk)

## Claim tuples

- H: Is the molecular emission in HD 100546 ringed, and how do the rings relate to the dust rings? | E: Imaged 19 species at about 0.3 arcsec, azimuthally averaged radial profiles and overplotted ring peaks on the continuum profile | R: Molecular rings at about 200-240 au peak just beyond the outer dust ring | F: Clear connection between the large dust distribution and the chemistry, but a deep gas gap alone cannot explain the rings | **supported**
- H: Do different emitting heights explain the differing ring peak locations? | E: Compared ring geometry with Z/R = 0, 0.1, 0.25 ellipses | R: Outer rings arise from Z/R < 0.1 | F: Emitting height is likely not responsible for the offsets in the outer disk | **supported**
- H: Are there azimuthal asymmetries in the molecular rings and SO emission? | E: Polar deprojections of integrated intensity maps for continuum and lines | R: Consistent azimuthal brightness asymmetry in outer rings, most prominent in radicals and CS; asymmetric SO within the cavity | F: Outer-ring asymmetry follows the dust; origin (shadowing, UV variation, column density following dust) not settled; SO asymmetry may link to a forming giant planet | **partially**
- H: Is the ionization tracer abundance and CN abundance in HD 100546 different from the MAPS Herbig disks? | E: Derived column densities and compared with HD 163296 and MWC 480 | R: Ion/CO about 1e-7, 1-3 orders of magnitude lower; CN 10-100x less abundant | F: Different ionization and a likely near-midplane CN layer in HD 100546; chemical modelling needed to test | **partially**
- H: Does the disk host complex organic chemistry comparable to other Herbig Ae disks? | E: Line search with matched filter and imaging; upper limits on undetected species | R: Methyl formate and another large organic detected; several COMs undetected, attributed to sensitivity | F: Hot corino-like chemistry may be active in the inner disk | **partially**

## Reasoning

- Why this data: Line-rich Band 7 data allow putting HD 100546 in context with other Class II disks  
  > "These line-rich data enable us to put the HD 100546 disk in proper context with other Class II disks" (Introduction)
- Why this method: Matched filtering suits weak, spatially extended, spectrally resolved emission; image-plane stacking used for compact weak lines  
  > "Since matched filtering works best for detecting weak emission that is spatially extended and spectrally resolved" (Weak-line detections / non-detections)
- Alternative: Azimuthal temperature variation as the cause of ring asymmetry is not supported by the optically thick tracer  
  > "The azimuthal asymmetries in the outer rings could be due to azimuthal variation in temperature, but the lack of clear signature in the optically thick does not support this." (The origin of the asymmetric molecular sub-structures in HD 100546)
- Alternative: Different emitting heights as the cause of ring-peak offsets rejected  
  > "Therefore, different emitting heights are likely not responsible for the different ring peak locations." (Sub-structures in the HD 100546 disk)
- How they decided it was enough: Self-calibration iterated until continuum S/N plateaued  
  > "until the signal-to-noise of the continuum data plateaued" (Data reduction)
- Limitation (authors): Resolution cannot resolve gas inside the cavity  
  > "cannot resolve the gas within the cavity" (Data reduction)
- Limitation (authors): Single transitions and fixed Tex; excitation conditions left to future work  
  > "Future work will focus specifically on constraining the excitation conditions of these molecules individually." (Column density calculations)
- Limitation (authors): Inner-disk column density ratios tentative due to possible optical thickness  
  > "For the inner disk these column density ratios are tentative due to potentially optically thick emission." (Column densities)
- Limitation (authors): No kinematic resolution to measure emitting heights directly  
  > "Although we do not have the kinematic resolution to directly measure the emitting heights of these different molecules from the channel maps" (Sub-structures in the HD 100546 disk)
- Caveat (inferred, ours): Column densities rest on assumed fixed Tex (30/50/100 K) and 1 km/s line width, so ratios carry large unquantified systematics
- Caveat (inferred, ours): Ring peak positions are compared at 0.3 arcsec resolution, so offsets of about half a beam are marginal
- Caveat (inferred, ours): Several weak detections (SO 9_8-8_7 at 4 sigma, tentative new species) depend on matched-filter choices
- Caveat (inferred, ours): Species names are missing from the converted text, so some key ratios cannot be attributed from the text alone

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Self-calibration solints, reference antenna and spw combination
- Missing: Line-free channel ranges for uvcontsub
- Missing: tclean image/cell size, scales and thresholds
- Missing: Matched-filter and GoFish settings (centres, inclinations, noise estimate)
- Missing: Spectroscopic database used for line parameters and partition functions
- Missing: Procedure for ring-peak radii and column density uncertainties
- Missing: Per-species numeric column density profiles (only plotted)
- Data volume (inferred): Nine execution blocks of Band 7 with 8 spectral windows each; likely a few hundred GB raw, tens of GB calibrated measurement sets
- Score (inferred): 3/5, Project code, CASA version, imaging robust, masks and self-cal scheme are given, but solints, channels, image sizes, line-list source and ring/column-density procedures are not; main results are mostly maps and profiles with few numeric tables.
- Rediscovery candidate: no, The paper does not state that the data are public, the recipe omits several needed settings, and many results are qualitative maps and plotted profiles.

## Links

- Method: Loomis et al. 2018b (cite: Loomis2018) (Matched filtering technique for weak line detection)
- Method: Loomis et al. 2018a (cite: 2018ApJ...859..131L) (Column density method including optical depth correction)
- Method: Teague 2019 (cite: GoFish) (GoFish spectral stacking tool)
- Method: Teague 2020 (cite: rich_teague_2020_4321137) (Keplerian mask generator)
- Companion: Booth et al. 2024 (cite: Booth2023_irs48) (Paper II presenting IRS 48 from the same ALMA program)
- Companion: Booth et al. 2023b (cite: Booth2023) (HD 169142 chemistry and SO asymmetry comparison)
- Companion: Booth et al. 2023a (cite: 2023A&A...669A..53B) (Earlier asymmetric SO in the HD 100546 cavity)
- Related: MAPS ALMA Large Program (HD 163296, MWC 480)
- Related: ALMA program 2021.1.00738.S (also IRS 48)

## Checks

```json
{
 "quotes": 124,
 "quotes_ok": 124,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 14,
 "numeric_problems": 0,
 "fill": {
  "facts": 107,
  "stated": 79,
  "rate": 0.738
 },
 "evidence_ok": true
}
```
