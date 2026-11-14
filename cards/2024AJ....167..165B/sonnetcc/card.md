# An ALMA Molecular Inventory of Warm Herbig Ae Disks. II. Abundant Complex Organics and Volatile Sulphur in the IRS 48 Disk

`2024AJ....167..165B` | The Astronomical Journal 2024 | first author: Booth, Alice S. | arXiv: 2402.04002 | DOI: 10.3847/1538-3881/ad26ff

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: Which molecules (simple species, complex organics, sulphur-bearing species) are present in the IRS 48 disk, where is each located relative to the dust trap, and what do their abundances imply about inherited and processed ices  
  > "Here, we present ALMA observations of the IRS 48 disk where we detect 16 different molecules" (abstract); "we further unravel the volatile sulphur and complex organic reservoir of the disk and discuss the physical/chemical origin of the molecular sub-structures observed" (Introduction)
- Target **IRS 48**: coordinates _not stated_; z/distance 135 pc (IRS 48; per the adopted pair 110 pc v 135 pc for HD 100546 v IRS 48)  
  > "After accounting for the different distances to the two sources (110 pc v 135 pc)" (Results (disk integrated line fluxes)); distance from _not stated_
- Target **HD 100546 (comparison disk, same program, presented in companion paper)**: coordinates _not stated_; z/distance 110 pc  
  > "compared to the HD 100546 disk, which was observed as part of the same ALMA program (cite: Booth2023_hd100546)" (Results (disk integrated line fluxes)); distance from _not stated_

## Data provenance

- ALMA projects: 2021.1.00738.S, 2017.1.00834.S
- bands: _not stated_
- frequencies and spectral setup: Two spectral settings (A and B), four spectral windows each, 976.6 kHz channels (0.84 km/s at 350 GHz); SPW centres 338.790824, 340.732413, 348.916936, 350.775389 GHz (setting A) and 344.240980, 354.367095, 356.067114 GHz plus a mistyped '3459.40999' GHz (setting B)  
  > "The data consist of two spectral settings with four spectral windows each at a spectral resolution of 976.6 kHz" (Observations); "These spectral windows are centered at 338.790824, 340.732413, 348.916936 and 350.775389 GHz for setting A" (Observations)
- continuum bandwidth: 1.875 GHz per spectral window  
  > "and a bandwidth of 1.875 GHz." (Observations)
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: about 0.3 arcsec  
  > "These $\approx$0.3$''$ data have a beam area 2.5$\times$ smaller than that presented the series of papers from" (Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: about 10 hours on-source across two programs (2017.1.00834.S and 2021.1.00738)  
  > "in only two ALMA observing programs (2017.1.00834.S, 2021.1.00738) with just $\approx$10 hours of on-source time" (Conclusion)
- observing dates: _not stated_
- pi or archival as stated: Program 2021.1.00738.S, PI A. S. Booth  
  > "IRS 48 was observed in the ALMA program 2021.1.00738.S (PI. A. S. Booth)" (Observations)
- Line: ethylene oxide two lines detected with the Keplerian matched filter (338.7720826 GHz and 350.3036524 GHz)
- Line: SO J=7_8-6_7 (representative, strongest); J=3_3-3_2 used for the column density (not stated)
- External data: Local ISM isotope ratio of 22 used to check that the SO line is optically thin  
  > "the ratio is consistent with 22, the local ISM" (Results (Column densities)) [from Wilson 1999 (cite: 1999RPPh...62..143W)]
- External data: Expected isotope ratio of 69 compared with the measured column density ratio  
  > "This is significantly lower than the expected / of 69 (cite: 1999RPPh...62..143W)" (Results (Column densities)) [from Wilson 1999 (cite: 1999RPPh...62..143W)]
- External data: HD 100546 data, line fluxes and column densities used for the IRS 48 comparison  
  > "compared to the HD 100546 disk, which was observed as part of the same ALMA program (cite: Booth2023_hd100546)" (Results (Disk integrated line fluxes)) [from Booth et al. 2024, submitted AJ (cite: Booth2023_hd100546)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Self-calibration on the line-flagged IRS 48 continuum: four rounds of phase and one round of amplitude calibration; continuum S/N rose from about 475 to about 3220  
  > "The self-calibration was performed on the IRS 48 continuum data after flagging the strong lines" (Observations); "This process consisted of four rounds of phase-calibration and one round of amplitude calibration" (Observations)

### Imaging

- task: CASA tclean  
  > "The data were imaged in CASA using" (Observations)
- deconvolver: multiscale, uniform velocity resolution of 0.9 km/s  
  > "with the multiscale deconvolver with a uniform velocity resolution of 0.9" (Observations)
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Keplerian masks built from the disk properties in the source table; cleaned down to 4x the rms of the dirty image  
  > "Individual lines were cleaned with Keplerian masks down to 4" (Observations); "the rms of the dirty image where the Keplerian masks were constructed using the properties for the IRS 48 disk" (Observations)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Full data reduction, observational set-up and imaging details are given in the companion paper  
  > "for full details the data reduction, observational set-up and imaging please refer to the companion paper which also presents data on the HD 100546 system (cite: Booth2023_hd100546)" (Observations) [from Booth2023_hd100546 (cite: Booth2023_hd100546)]
- Column densities estimated following Loomis et al. 2018a and in the same manner as for HD 100546  
  > "We estimate column densities following the methods outlined in (cite: 2018ApJ...859..131L) and in the same manner as (cite: Booth2023_hd100546)." (Results (Column densities)) [from (cite: 2018ApJ...859..131L); (cite: Booth2023_hd100546)]
- Matched filtering used for the initial line identification  
  > "We use matched filtering to make an initial line identification (cite: Loomis2018)." (Results (Molecules detected)) [from (cite: Loomis2018)]
- Upper limit on undetected line fluxes propagated from channel-map rms and mask pixel count  
  > "If a molecule is undetected we give the 3 $\sigma$ upper limit on the flux where $\sigma$ is propagated from the rms in the channel maps and the number of pixels included in the mask (cite: 2019A&A...623A.124C)" (Results (Disk integrated line fluxes)) [from (cite: 2019A&A...623A.124C)]
- Representative transitions chosen from the strongest lines detected in HD 100546  
  > "These representative transitions are based on the strongest lines detected in the HD 100546 disk." (Results (Disk integrated line fluxes)) [from (cite: Booth2023_hd100546)]

### Not stated but needed to reproduce (our reading)

- CASA version and whether the pipeline or manual calibration was used (deferred to the companion paper)
- Line-free channels used to flag lines before the continuum self-calibration and the solution intervals of the four phase rounds and the amplitude round
- Phase centre coordinates of IRS 48 and the source of its adopted distance, inclination and position angle (table refs [1-7] are not resolvable from the text)
- Exact Keplerian mask parameters (inner and outer radius, line width) for each line, and the method used to subtract the continuum
- Spectroscopic database and rest frequencies per species (molecule names are missing in the converted text)
- Procedure and code used for matched-filter cross-correlation and for the azimuthal and polar deprojection of the intensity maps
- Details of the column density calculation (partition functions, line width, beam dilution treatment) beyond reference to Loomis et al. 2018a and the companion paper
- Flux calibration scale uncertainty

## Analysis recipe

1. **Calibrate, self-calibrate and image the line cubes**: Self-calibration on the line-flagged continuum, then tclean imaging of each line with the multiscale deconvolver and Keplerian masks  
  > "The self-calibration was performed on the IRS 48 continuum data after flagging the strong lines" (Observations); "with the multiscale deconvolver with a uniform velocity resolution of 0.9" (Observations)
   - software: CASA, tclean
   - parameter: Four rounds of phase and one round of amplitude self-calibration  
  > "This process consisted of four rounds of phase-calibration and one round of amplitude calibration" (Observations)
   - parameter: Cleaned down to 4x the rms of the dirty image with Keplerian masks  
  > "Individual lines were cleaned with Keplerian masks down to 4" (Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Identify and detect molecules by matched filtering**: Cross-correlate the uv data with a Keplerian model filter (outer radius 150 au); detection is a response of at least 4 sigma  
  > "This technique uses the predictable Keplerian rotation of the disk gas to detect molecular lines in the visibility data via cross correlation of the uv-data with a filter." (Results (Molecules detected)); "a detection is defined as a matched filter response of at least 4 $\sigma$" (Results (Molecules detected))
   - parameter: Keplerian filter with outer radius of 150 au (IRS 48) versus 300 au (HD 100546)  
  > "for the IRS 48 disk with a Keplerian model with an outer radius of 150 au compared to the HD 100546 response (outer radius of 300 au)" (Results (Molecules detected))
   - fitting: _not stated_
   - validation: Alternative image filters were tried for one molecule and gave no significant improvement; channel maps show 4 sigma emission over 3 consecutive channels for the new detection  
  > "Using alternative image filters does not yield a significant improvement in the detection strength" (Results (Molecules detected)); "compact emission from is detected at the 4 $\sigma$ level over the 3 consecutive channels where the lines are strongest for both lines" (Results (Molecules detected))
3. **Make integrated intensity maps of each molecule**: Moment-zero maps of a representative transition per molecule using the Keplerian masks from CLEANing with no clipping thresholds  
  > "These line maps were generated using the Keplerian masks generated in the CLEANing with no clipping thresholds." (Results (Integrated intensity maps))
   - fitting: _not stated_
   - validation: _not stated_
4. **Measure azimuthal and radial sub-structure**: Azimuthal profiles at the radius where each molecule peaks, compared with the normalised millimetre dust profile; polar deprojection of the intensity maps  
  > "at the radius where each of the molecules peak along with the normalised azimuthal profile of the millimetre dust." (Results (Sub-structures)); "which presents a polar deprojection of the intensity maps" (Results (Sub-structures))
   - fitting: _not stated_
   - validation: _not stated_
5. **Measure disk-integrated line fluxes and compare with HD 100546**: Fluxes extracted from Keplerian masks of 2.0 arcsec (IRS 48) and 4.0 arcsec (HD 100546) radius; non-detections get 3 sigma upper limits; fluxes normalised to a CO isotopologue line to account for different gas masses  
  > "These fluxes are extracted from Keplerian masks which are 2.0$''$ and 4.0$''$ in radius for the IRS 48 and HD 100546 disks, respectively." (Results (Disk integrated line fluxes)); "we normalise the line fluxes with respect to the $J=3-2$ line" (Results (Disk integrated line fluxes))
   - assumption: The normalising CO isotopologue flux is a good proxy for total gas content in each disk  
  > "this flux should be a good proxy for the total gas content in each disk (cite: 2021ApJS..257....5Z)" (Results (Disk integrated line fluxes))
   - fitting: _not stated_
   - validation: Paper notes caveats for the comparison from possible optical thickness and different excitation temperatures  
  > "There are caveats to this comparison, e.g., if lines are optically thick in one or both of the disks and/or the excitation temperatures are very different." (Results (Disk integrated line fluxes))
6. **Derive azimuthal column density profiles and ratios**: Column densities per Loomis et al. 2018a for one representative transition per molecule, at excitation temperatures of 50, 100 and 150 K; upper limits from disk-integrated flux limits  
  > "explore a range of excitation temperatures: 50, 100 and 150 K" (Results (Column densities)); "We estimate column densities following the methods outlined in (cite: 2018ApJ...859..131L)" (Results (Column densities))
   - parameter: Excitation temperatures 50, 100 and 150 K  
  > "explore a range of excitation temperatures: 50, 100 and 150 K" (Results (Column densities))
   - assumption: ISM isotope ratios used to convert the isotopologue column to a CO column  
  > "With the assumption of ISM isotope ratios" (Results (Column densities))
   - assumption: Upper limits assume an emitting area of a 2 arcsec aperture  
  > "assuming a conservative emitting area of a 2" aperture" (Results (Column densities))
   - fitting: _not stated_
   - validation: Optical depth checked via isotopologue and isotope-ratio comparisons (e.g. SO consistent with 22)  
  > "the ratio is consistent with 22, the local ISM" (Results (Column densities))
7. **Compare abundance ratios with HD 100546, protostars and comets**: Compare peak column density ratios (COMs, sulphur species) to values from HD 100546, protostar IRAS 16293-2422 and comet 67P in the literature  
  > "With this family of molecules, we can compare the relative column density ratios of these species to both protostars and comets." (Discussion (volatile sulphur))
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Imaging with tclean, multiscale deconvolver  
  > "The data were imaged in CASA using" (Observations)
- **Astropy** : _not stated_
- **IPython** : _not stated_
- **Jupyter** : _not stated_
- **Matplotlib** : _not stated_
- **NumPy** : _not stated_

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of molecular species detected in IRS 48 | 16 | not stated | molecules | 2 | we have detected 16 molecular species in IRS 48 disk |
| Continuum S/N before and after self-calibration | about 475 to about 3220 | not stated | dimensionless | 1 | continuum signal-to-noise increase from $\approx$475 to $\approx$3220 |
| Peak column density of a CO isotopologue (species name missing in text) at 100 K | 2.5e16 | not stated | cm^-2 | 6 | The peak column density is $\approx2.5\times10^{16}$ $\mathrm{cm^{-2}}$ at 100 K and the line is optically thin. |
| Equivalent CO column density | 5e19 | not stated | cm^-2 | 6 | this is equivalent to a CO column density of $\approx5\times10^{19}$ $\mathrm{cm^{-2}}$ |
| Peak SO column density (J=3_3-3_2) at 100 K | 5e15 | not stated | cm^-2 | 6 | This results in a peak column density of $5\times10^{15}~\mathrm{cm^{-2}}$ at 100 K. |
| Peak CS column density | about 1e13 | not stated | cm^-2 | 6 | The radical CS is detected with a peak column density of $\approx10^{13}~\mathrm{cm^{-2}}$ |
| N(CS)/N(SO) | about 1e-3 | not stated | dimensionless | 6 | results in a N(CS)/N(SO)$\approx10^{-3}$ |
| OCS column density upper limit | <1e12 | not stated | cm^-2 | 6 | OCS is not detected with a column density upper limit of $<10^{12}$ $\mathrm{cm^{-2}}$ |
| Peak abundance ratios of three COMs relative to a reference species at 100 K (species names missing in converted text) | 0.28; 0.25; 0.017 | 0.04; 0.03; 0.006 | dimensionless | 6 | are $0.28\pm0.04$, $0.25\pm0.03$ and $0.017\pm0.006$, respectively, at a temperature of 100 K. |
| Column density ratio of an isotopologue pair (names missing), main isotopologue case | 14 | 1 | dimensionless | 6 | results in a column density ratio of / of 14$\pm1$ |
| Same ratio using a C isotope ratio of 69 | 0.8 | 0.1 | dimensionless | 6 | results in a ratio of 0.8$\pm0.1$ |
| Disk-averaged 3 sigma upper limit on CN column density | <=2e12 | not stated | cm^-2 | 6 | 3 $\sigma$ disk-averaged upper limit of CN $\leq2\times10^{12}$ $\mathrm{cm^{-2}}$ |
| Largest disk-averaged line-ratio difference between IRS 48 and HD 100546 | about 130x higher in IRS 48 | not stated | dimensionless | 5 | is $\approx$130$\times$ higher in IRS 48 than HD 100546. |
| Peak sulphur column density ratios (first species name missing) /SO, CS/SO | about 26%; about 0.2% | not stated | percent | 7 | peak column density ratios of /SO of $\approx$26%, CS/SO of $\approx$0.2% |

## Qualitative findings

- All molecular emission except CO is co-located with the dust trap in the south of the disk  
  > "All of the molecular emissions, aside from CO, are co-located with the dust trap" (abstract)
- COM emission is azimuthally narrower and peaks with the dust; sulphur species are more azimuthally extended and radially farther from the star  
  > "with the latter being more azimuthally extended and radially located further from the star" (abstract)
- IRS 48 hosts three COMs of 7 or more atoms plus the first heterocycle in a protoplanetary disk  
  > "is the first detection of a heterocyclic molecule in a protoplanetary disk" (Discussion (molecular complexity))

## Claim tuples

- H: What molecules are present in the IRS 48 disk? | E: ALMA band 7 line survey, matched filter detection at 4 sigma | R: 16 species detected including first robust detections of three species | F: IRS 48 is the most chemically rich disk studied so far | **supported**
- H: Is molecular emission tied to the dust trap? | E: Integrated intensity maps and azimuthal profiles compared with the millimetre dust | R: All emission except CO lies in the same region as the dust trap | F: Strong coupling between dust and ice chemistry | **supported**
- H: Do different molecular families share the same spatial distribution? | E: Azimuthal profiles and polar deprojection of intensity maps | R: Radial and azimuthal offsets between COMs and the SO-type sulphur species | F: Different chemical origins or processes may be at work; chemistry in turbulent vortices needs further study | **supported**
- H: Do COM abundances relative to the reference species exceed protostellar values, implying ice processing in the disk? | E: Peak column density ratios at 50-150 K compared with protostar values from the literature | R: Ratios of about 0.28, 0.25 and 0.017 are higher than the few percent seen in protostars | F: May indicate processing of inherited ices, but could be an artefact of optically thick, beam-diluted emission | **partially**
- H: Is the volatile sulphur reservoir like that of protostars and comets? | E: Compare peak column density ratios of SO, CS, OCS and other S species with literature values | R: OCS and one other S species undetected; OCS/SO below 0.3% | F: Partition of volatile sulphur is distinct from comets and protostars | **supported**

## Reasoning

- Why this data: Warm Herbig Ae transition disks with a rich chemistry offer a view of a normally unobservable ice-derived reservoir  
  > "These sources therefore give us a window into a typically unobservable molecular reservoir in disks." (Introduction)
- Why this method: Matched filtering exploits Keplerian rotation to detect weak lines in the visibilities  
  > "This technique uses the predictable Keplerian rotation of the disk gas to detect molecular lines in the visibility data" (Results (Molecules detected))
- Alternative: Dip in line intensity at the dust peak may be line suppression from optically thick dust  
  > "This could be due to line suppression from the optically thick dust" (Results (Sub-structures))
- How they decided it was enough: _not stated_
- Limitation (authors): Comparison with HD 100546 is subject to optical depth and excitation temperature differences  
  > "There are caveats to this comparison, e.g., if lines are optically thick in one or both of the disks and/or the excitation temperatures are very different." (Results (Disk integrated line fluxes))
- Limitation (authors): COM abundances may be underestimated in column density because of optically thick and beam-diluted emission; isotopologue observations are needed  
  > "Deeper observations to target isotopologues are needed to test this." (Discussion (molecular complexity))
- Caveat (inferred, ours): Column densities use a single representative transition and a fixed set of excitation temperatures, with no fit or covariance treatment
- Caveat (inferred, ours): Line optical depth and beam dilution are not modelled, so COM abundance ratios are loosely constrained
- Caveat (inferred, ours): Unresolved target coordinates, distance source and flux calibration uncertainty are not given in this paper
- Caveat (inferred, ours): Two projects are cited but only 2021.1.00738.S is described in the Observations section

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Detailed calibration, line-free channel selection and self-calibration solution intervals (in the companion paper or not given)
- Missing: Molecule names and database sources in the converted text are partly missing
- Missing: Matched-filter and column density code are not named or released in this paper
- Data volume (inferred): Eight execution blocks of ALMA Band 7 data for two settings (about 10 hours on source); likely tens of GB of raw visibilities
- Score (inferred): 2/5, Project code and imaging recipe are given but calibration details are deferred to a companion paper and column density details to a cited method; key parameters (line-free channels, masks, solints) are missing
- Rediscovery candidate: no, Public status of the data is not stated and the recipe depends on an unpublished companion paper, so the numeric results cannot be redone from this text alone

## Links

- Method: Loomis et al. 2018b (cite: Loomis2018) (Matched filter line identification)
- Method: Loomis et al. 2018a (cite: 2018ApJ...859..131L) (Column density method)
- Companion: Booth et al. 2024 (cite: Booth2023_hd100546) (Companion paper with the data reduction, observational set-up and the HD 100546 results)
- Related: ALMA program 2017.1.00834.S
- Related: Booth et al. HD 100546 molecular inventory (paper I)

## Checks

```json
{
 "quotes": 84,
 "quotes_ok": 84,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 14,
 "numeric_problems": 0,
 "fill": {
  "facts": 94,
  "stated": 46,
  "rate": 0.489
 },
 "evidence_ok": true
}
```
