# Pristine ices in a planet-forming disk revealed by heavy water

`2025NatAs...9.1486L` | Nature Astronomy 2025 | first author: Leemker, Margot | arXiv: 2510.19919 | DOI: 10.1038/s41550-025-02663-y

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: Is the water ice in the outbursting V883 Ori disk inherited from the cold cloud or reset? Tested by detecting doubly deuterated water (D2O) and measuring D2O/H2O and (D2O/HDO)/(HDO/H2O) ratios.  
  > "the most sensitive tracer to distinguish inheritance from reprocessing to shed light on the origin of ices in disks, in particular the origin of water ice" (Introduction)
- Target **V883 Ori disk**: coordinates _not stated_; z/distance 400 pc  
  > "This star is located at 400 pc (1300 ly) in the Orion molecular cloud" (Results); distance from _not stated_

## Data provenance

- ALMA projects: 2023.1.00588.S, 2021.1.00186.S
- bands: Band 7 (D2O 316.8 GHz, new data); HDO and H2-18-O from Band 6 and Band 5 (reimaged archival data)  
  > "We observed the V883 Ori disk in ALMA band 7 for 2.4 hours on source" (Methods, Self-calibration); "5% absolute flux calibration uncertainty for ALMA Band 5 and 6 (HDO and H$_2^{18}$O) and 10% for ALMA Band 7" (Methods, Flux measurements)
- frequencies and spectral setup: D2O 1(1,0)-1(0,1) at 316.7998 GHz, 61 kHz (58 m/s) resolution, 117.2 MHz bandwidth; continuum window 1.875 GHz wide centred at 315 GHz; six further windows at 122 kHz resolution, 58.6 MHz bandwidth; one at 328.857 GHz with 117.2 MHz  
  > "at 316.7998 GHz at a spectral resolution of 61 kHz (58 m s$^{-1}$) and a total bandwidth of 117.2 MHz" (Methods, Self-calibration); "A continuum spectral window covering 1.875 GHz of bandwidth at a spectral resolution of 1.1 km s$^{-1}$ was centered at 315 GHz." (Methods, Self-calibration)
- continuum bandwidth: 180 MHz used for self-calibration (reduced because the disk is line rich)  
  > "Since this is a very line-rich disk, the total continuum bandwidth used for the self-calibration is reduced to 180 MHz." (Methods, Self-calibration)
- arrays: _not stated_
- configurations: _not stated_
- baselines: minimum 15.1 m; maximum 1.2 km (24 Dec 2023) and 1.4 km (28 and 30 Jul 2024)  
  > "24 Dec. 2023 | 43 | 15.1 | 1.2 | J0423-0120 | J0607-0834" (Supplementary Table 4); "28 Jul. 2024 | 45 | 15.1 | 1.4 | J0538-4405 | J0607-0834" (Supplementary Table 4)
- angular resolution: D2O beam 0.24 x 0.19 arcsec (89 deg) at robust = 0  
  > "resulting in a $0\ensuremath{\overset{\prime\prime}{.}}24 \times 0\ensuremath{\overset{\prime\prime}{.}}19\ (89\degree)$ beam" (Methods, Imaging)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 2.4 hours on source over three execution blocks (Band 7, 2023.1.00588.S)  
  > "ALMA band 7 for 2.4 hours on source distributed over three execution blocks" (Methods, Self-calibration)
- observing dates: 24 Dec 2023, 28 Jul 2024, 30 Jul 2024 (Band 7 execution blocks)  
  > "24 Dec. 2023 | 43 | 15.1 | 1.2 | J0423-0120 | J0607-0834" (Supplementary Table 4); "30 Jul. 2024 | 47 | 15.1 | 1.4 | J0538-4405 | J0607-0834" (Supplementary Table 4)
- pi or archival as stated: 2023.1.00588.S (PI M. Leemker, D2O data); 2021.1.00186.S (PI J. J. Tobin, HDO and H2-18-O data re-imaged)  
  > "2023.1.00588.S; PI: M. Leemker" (Methods, Self-calibration); "we re-imaged the HDO and H$_2^{18}$O data presented in (2021.1.00186.S; PI: J. J. Tobin)" (Methods, Imaging)
- Line: D2O 1(1,0)-1(0,1) (316.7998 GHz)
- Line: HDO 3(1,2)-2(2,1) (225.8967 GHz)
- Line: H2-18-O 3(1,3)-2(2,0) (203.4075 GHz)
- Line: HDO 241 GHz line (second HDO line, not used in flux analysis) (241 GHz)
- External data: HDO excitation temperature of 199 +/- 42 K from two HDO lines, adopted for all water isotopologues  
  > "we use the excitation temperature of $199\pm 42$ K of the HDO molecule" (Results) [from not stated (citation not preserved in the text)]
- External data: Source geometry and mass: distance 400 pc, stellar mass 1.3 Msun, inclination 38.3 deg, position angle 32 deg  
  > "using a distance of 400 pc , a stellar mass of 1.3 M$_{\odot}$, a disk inclination of 38.3$\degree$, and a position angle of 32$\degree$" (Methods, Flux measurements) [from not stated (citations not preserved in the text)]
- External data: ISM ratio N(H2-16-O)/N(H2-18-O) = 560 +/- 25 used to scale to total H2O column  
  > "using the typical ratio of $560 \pm 25$ in the ISM" (Results) [from not stated (citation not preserved in the text)]
- External data: Class 0 comparison values: D2O/H2O = (2-9)e-5 and (D2O/HDO)/(HDO/H2O) = 2.2-7.1  
  > "$(2-9)\times 10^{-5}$ and (/HDO) / (HDO/) = $2.2-7.1$ in younger Class 0 objects" (Discussion) [from not stated (citation not preserved in the text)]
- External data: Comet 67P D2O/H2O = (1.9 +/- 1.0)e-5  
  > "$(1.9 \pm 1.0)\times 10^{-5}$ in the comet 67 P" (Discussion) [from not stated (citation not preserved in the text)]
- External data: Comet 67P HDO/H2O of (1.06 +/- 0.14)e-3 used for a consistent analysis of ratios  
  > "we use previously derived HDO/ ratio of $(1.06 \pm 0.14) \times 10^{-3}$ for a consistent analysis across all water isotopologue ratios measured in this comet" (Supplementary, HDO/H2O ratio) [from not stated (citation not preserved in the text)]
- Simulation/model as data: Chemical model of a collapsing core (gas parcels post-processed with deuterium chemistry network) giving D2O/H2O and double-ratio ranges for inheritance (<~10% of ice destroyed) and reset (>~70% destroyed)  
  > "based on chemical modelling of gas and ice in a collapsing core" (Discussion); "inheritance (all stream lines where $\lesssim 10$% of the water ice is destroyed) or reset (all stream lines where $\gtrsim 70$% of the water ice is destroyed)" (Discussion)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 6.5.4  
  > "The data were self-calibrated using CASA version 6.5.4 following the analysis used in the exoALMA large program" (Methods, Self-calibration)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0423-0120 (24 Dec 2023); J0538-4405 (28 and 30 Jul 2024), listed as bandpass and flux calibrator  
  > "24 Dec. 2023 | 43 | 15.1 | 1.2 | J0423-0120 | J0607-0834" (Supplementary Table 4); "28 Jul. 2024 | 45 | 15.1 | 1.4 | J0538-4405 | J0607-0834" (Supplementary Table 4)
- flux scale uncertainty: 5% (Band 5 and 6), 10% (Band 7); EB of 24 Dec 2023 rescaled down by 8.6% before self-calibration  
  > "5% absolute flux calibration uncertainty for ALMA Band 5 and 6 (HDO and H$_2^{18}$O) and 10% for ALMA Band 7" (Methods, Flux measurements); "the data taken on December 24th 2023 had an 8.6% higher amplitude across all baselines" (Methods, Self-calibration)
- self calibration: Per EB: 1 phase round (solint = EB length, 1 h 19 min). After alignment and concatenation: 7 phase-only rounds (EB length, 360, 120, 60, 20, 10, 6 s), then 1 phase+amplitude round (solint = EB length); robust 0.5; mask 0.6 arcsec semi-major; solutions deviating >~20% in amplitude flagged  
  > "After combining all execution blocks, seven rounds of phase-only self-calibration were performed with solution intervals with the length of a single EB, 360, 120, 60, 20, 10, and 6 seconds." (Methods, Self-calibration); "seven rounds of phase-only self-calibration and a single round of phase and amplitude self-calibration with separate solutions for both polarizations" (Methods, Self-calibration); "Solutions deviating by more than $\sim$20% in amplitude were flagged." (Methods, Self-calibration)

### Imaging

- task: CASA tclean, Briggs weighting  
  > "The line itself was imaged using the CASA task `tclean` with Briggs weighting" (Methods, Imaging)
- deconvolver: _not stated_
- weighting robust: D2O robust = 0; H2-18-O robust = 1.0; HDO robust = 2.0 (in the order of the sentence); self-calibration imaging robust = 0.5  
  > "Briggs weighting and a `robust` parameter of 0, which provides the best balance between spatial resolution and noise" (Methods, Imaging); "when cleaned with a `robust` parameter of 1.0 and 2.0, respectively" (Methods, Imaging); "We employed Briggs weighting with `robust`$=0.5$." (Methods, Self-calibration)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: No uvcontsub (too few line-free channels). Per EB: mtmfs (nterms = 2) image of line-free channels, model added with ft, subtracted with uvsub  
  > "too few line-free channels were available to subtract the continuum emission in the $uv$-plane using the standard CASA task `uvcontsub`" (Methods, Continuum subtraction); "The resulting model for the continuum emission was added to the measurement set using `ft`" (Methods, Continuum subtraction); "This model was then used to subtract the continuum using the CASA task `uvsub`." (Methods, Continuum subtraction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Final cube channel spacing 400 m/s (to match HDO and H2-18-O); Keplerian masks convolved with a Gaussian 0.5 (D2O), 1.25 (HDO), 0.75 (H2-18-O) times the beam  
  > "The channel spacing for the final image is 400 m s$^{-1}$ to match that of the HDO and H$_2^{18}$O data." (Methods, Imaging); "the mask is convolved with a Gaussian 0.5 (), 1.25 (HDO), and 0.75 (H$_2^{18}$O) times larger than the beam of the respective observations" (Methods, Flux measurements)
- final beam: D2O 0.24 x 0.19 (89 deg); H2-18-O 0.13 x 0.11 (-72 deg); HDO 0.10 x 0.08 (-78 deg)  
  > "resulting in a $0\ensuremath{\overset{\prime\prime}{.}}24 \times 0\ensuremath{\overset{\prime\prime}{.}}19\ (89\degree)$ beam" (Methods, Imaging); "$0\ensuremath{\overset{\prime\prime}{.}}13\times  0\ensuremath{\overset{\prime\prime}{.}}11 (-72\degree)$ and $0\ensuremath{\overset{\prime\prime}{.}}10\times 0\ensuremath{\overset{\prime\prime}{.}}08 (-78\degree)$ for the H$_2^{18}$O and the HDO" (Methods, Imaging)
- final rms: _not stated_

### Inherited from earlier work

- Self-calibration procedure follows the exoALMA large-program analysis, with several routines from other work  
  > "following the analysis used in the exoALMA large program outlined in , with several routines by" (Methods, Self-calibration) [from exoALMA large program (citation not preserved in the text)]
- HDO excitation temperature (199 +/- 42 K) from a rotational diagram of two HDO lines in earlier work on this disk  
  > "the excitation temperature derived by from two HDO transitions with different upper energy levels is used for all analyzed lines" (Methods, Column density estimates) [from not stated (citation not preserved in the text)]
- HDO and H2-18-O data (project 2021.1.00186.S) were first presented earlier and are re-imaged here  
  > "we re-imaged the HDO and H$_2^{18}$O data presented in (2021.1.00186.S; PI: J. J. Tobin)" (Methods, Imaging) [from earlier paper on project 2021.1.00186.S (PI J. J. Tobin); citation not preserved in the text]
- Keplerian mask construction follows earlier work, using a named package (name not preserved)  
  > "The Keplerian masks are constructed using the package by following using a distance of 400 pc" (Methods, Flux measurements) [from not stated (package and citation not preserved in the text)]
- Collapsing-core chemical model comparison (inheritance vs reset ranges)  
  > "based on chemical modelling of gas and ice in a collapsing core" (Discussion) [from not stated (citation not preserved in the text)]

### Not stated but needed to reproduce (our reading)

- Name and version of the package used to build the Keplerian masks and the code for the pixel-by-pixel velocity shifting
- Which channels were flagged as line-free for the pseudo-continuum and for the mtmfs continuum model
- tclean image size, cell size, niter, clean mask and the numeric 1 sigma threshold for the line cubes
- Line-cube velocity range and reference frame/rest frequency handling for the cubes
- Standard calibration route (pipeline vs manual) and pipeline/CASA version for the delivered data, and calibration/imaging details for the 2021.1.00186.S HDO and H2-18-O data (CASA version, calibrators, self-calibration)
- Exact exoALMA self-calibration routines and settings not in the text
- Mirroring boundaries and regions used to build COM line templates, and the template regions for D2O and H2-18-O
- How partition functions at 199 K were obtained (Table 1 lists Q only at 300, 150 and 75 K)
- Source of the rotational-diagram temperature and its full fit setup
- Primary-beam correction details for the flux measurement

## Analysis recipe

1. **Self-calibrate Band 7 data**: Pseudo-continuum MS per EB from line-free channels; per-EB phase self-cal, EB alignment to the highest S/N EB, concatenation, 7 phase-only rounds and 1 phase+amplitude round; solutions applied to the full dataset  
  > "A pseudo-continuum Measurement Set was created for each EB after carefully flagging all spectral regions exhibiting line emission" (Methods, Self-calibration); "The solutions were then applied to the full dataset, following the same logical order as for the pseudo continuum Measurement Set." (Methods, Self-calibration)
   - software: CASA 6.5.4
   - parameter: Briggs robust = 0.5; clean model made inside an elliptical mask of 0.6 arcsec semi-major axis, PA 32 deg, inclination 38.3 deg  
  > "We employed Briggs weighting with `robust`$=0.5$." (Methods, Self-calibration); "constructed over an elliptical mask of $0\ensuremath{\overset{\prime\prime}{.}}6$ in semi-major axis" (Methods, Self-calibration)
   - parameter: Phase model cleaned to 6 sigma; amplitude model cleaned to 1 sigma  
  > "The model was created by cleaning the emission in all line-free channels down to a conservative threshold of $6\sigma$." (Methods, Self-calibration); "The model for the amplitude self-calibration was created by cleaning the line-free channels down to a $1\sigma$ threshold" (Methods, Self-calibration)
   - parameter: EB of 24 Dec 2023 flux rescaled (8.6% higher amplitude) before self-calibration  
  > "we rescaled the flux before self-calibration in this execution block" (Methods, Self-calibration)
   - fitting: _not stated_
   - validation: Peak S/N improved from 495 to 1457 with phase self-calibration; amplitude plus phase improved it by a further 3%  
  > "The phase self-calibration improved the peak signal-to-noise ratio of the data by a factor of 186%, from a peak signal-to-noise ratio of 495 to one of 1457." (Methods, Self-calibration)
2. **Subtract continuum from line data**: Per EB: mtmfs (nterms = 2) continuum model from line-free channels, ft into the MS, uvsub; EBs then combined  
  > "a mtmfs image up to and including first order (`nterms` $=2$) was created using the line free channels in the spectral window" (Methods, Continuum subtraction); "The resulting MS tables for all three EBs were then combined to make the final continuum subtracted dataset" (Methods, Continuum subtraction)
   - software: CASA, tclean (mtmfs), ft, uvsub
   - parameter: nterms = 2  
  > "a mtmfs image up to and including first order (`nterms` $=2$)" (Methods, Continuum subtraction)
   - fitting: _not stated_
   - validation: _not stated_
3. **Image D2O cube and re-image HDO and H2-18-O cubes**: tclean with Briggs weighting, cleaned to 1 sigma; D2O robust 0, H2-18-O robust 1.0, HDO robust 2.0; 400 m/s channels for channel maps and masks; native resolution used for shifted cubes  
  > "The line itself was imaged using the CASA task `tclean` with Briggs weighting" (Methods, Imaging); "In this work, these data are cleaned down to $1\sigma$, similar to the line" (Methods, Imaging)
   - software: CASA tclean
   - parameter: Cleaned to 1 sigma to capture all flux and be independent of non-Gaussian beam features  
  > "The image is cleaned down to $1\sigma$ to capture all the flux in the model and make the final measurement independent of any non-Gaussian features in the beam" (Methods, Imaging)
   - parameter: Native spectral resolution 58, 162, 180 m/s (D2O, HDO, H2-18-O) for the shifted cubes  
  > "the native spectral resolution of the data of 58, 162, and 180 m s$^{-1}$ for , HDO, and H$_2^{18}$O, respectively, is used" (Methods, Imaging)
   - fitting: _not stated_
   - validation: _not stated_
4. **Measure line fluxes with Keplerian masks (fiducial)**: Compute region in RA/Dec where each molecule should emit given disk Keplerian rotation in each channel; sum flux inside mask over channels 1.2-6.4 km/s; mask also shifted to COM line frequencies to test contamination  
  > "the lines are separated in the image plane by computing the region in Right Ascension and Declination where a molecule is expected to emit based on the Keplerian rotation of the disk" (Methods, Flux measurements); "The effect of neighboring COMs is investigated using an identical mask but then shifted to the frequency of those lines." (Methods, Flux measurements)
   - software: Keplerian mask package (name not preserved in text)
   - parameter: distance 400 pc, stellar mass 1.3 Msun, inclination 38.3 deg, PA 32 deg, emitting region 40-120 au, z/r = 0.4  
  > "an emitting region extending from 40 au to 120 au tracing $z/r=0.4$" (Methods, Flux measurements); "a stellar mass of 1.3 M$_{\odot}$, a disk inclination of 38.3$\degree$, and a position angle of 32$\degree$" (Methods, Flux measurements)
   - parameter: line width 350 m/s x sqrt(40 au / r); mask shifted by systemic velocity 4.3 km/s  
  > "The line width is assumed to follow 350 m s$^{-1} \times \sqrt{40~\mathrm{au}/r}$" (Methods, Flux measurements); "the mask is shifted by 4.3 km s$^{-1}$ to match the systemic velocity of V883 Ori" (Methods, Flux measurements)
   - parameter: Mask convolved with Gaussian 0.5 (D2O), 1.25 (HDO), 0.75 (H2-18-O) x beam, chosen by visual inspection; channels 1.2-6.4 km/s used  
  > "This parameter is chosen after visual inspection of the data." (Methods, Flux measurements); "To measure the disk integrated flux, only the channels between 1.2 and 6.4 km s$^{-1}$ are used" (Methods, Flux measurements)
   - assumption: Emission from disk at 40-120 au on a z/r = 0.4 surface; same mask parameters for all three isotopologues  
  > "These parameters are identical between all three analyzed water isotopologues." (Methods, Flux measurements)
   - fitting: _not stated_
   - validation: Flux uncertainty from rms of masks shifted to 8 positions at 1.4 arcsec and five velocities (40 non-overlapping locations); compared against the spectral-shifting method (consistent within 3 sigma)  
  > "the rms of the flux measured in masks shifted to eight different positions" (Methods, Flux measurements); "and to five different velocities resulting in 40 unique, non-overlapping locations" (Methods, Flux measurements)
5. **Measure line fluxes from Keplerian-shifted spectra (cross-check)**: Shift each pixel by the projected Keplerian velocity, extract disk-integrated spectrum in an elliptical region (0.4 arcsec semi-major axis), mirror the non-blended side of each COM line and subtract it, build line templates for D2O and H2-18-O from their clean sides  
  > "Each pixel is shifted to correct for the projected Keplerian velocity expected at this location in the disk." (Methods, Flux measurements); "The non-blended side of COM emission line is mirrored in the line center creating a symmetric line profile that is then subtracted from the shifted spectrum." (Methods, Flux measurements)
   - software: not stated (custom code, available on request)
   - parameter: Noise from rms of 520 independent shifted spectra in a 19 arcsec square without primary beam correction, excluding the inner 2.4 arcsec square  
  > "the noise is estimated using the rms of 520 independent shifted spectra extracted from a 19" square in the cube without primary beam correction" (Results)
   - assumption: Emission assumed to originate from the disk midplane  
  > "the emission is assumed to be originating from the disk midplane" (Methods, Flux measurements)
   - fitting: _not stated_
   - validation: Two methods consistent within 3 sigma; Keplerian-mask fluxes adopted because some flux may be lost to beam smearing in shifted spectra  
  > "The two methods to measure the line fluxes are consistent within $\leq 3\sigma$ for all three water isotopologues." (Methods, Flux measurements)
6. **Convert line fluxes to column densities and isotopologue ratios**: Optically thin LTE: N_u from integrated flux, Einstein A and emitting solid angle, then N_tot via partition function at rotational temperature 199 K; H2-18-O column scaled to H2-16-O with 560; ortho/para corrections  
  > "In this work, optically thin emission and local thermodynamical equilibrium (LTE) are assumed for this conversion." (Methods, Column density estimates); "The column density of the upper energy level can be determined without any knowledge on the rotational temperature" (Methods, Column density estimates)
   - software: not stated
   - parameter: Excitation temperature 199 +/- 42 K for all isotopologues  
  > "we use the excitation temperature of $199\pm 42$ K of the HDO molecule" (Results)
   - parameter: Emitting area equal to an ellipse of 0.4 arcsec (160 au) radius in the disk frame  
  > "an elliptical emitting region with that radius is used" (Methods, Column density estimates); "assuming an emitting area equal to the elliptical region used to extract the spectrum" (Results)
   - parameter: Ortho-to-para ratio 2 (D2O) and 3 (H2-18-O); N(H2-16-O)/N(H2-18-O) = 560 +/- 25  
  > "using a thermalized ortho-to-para ratio of 2 and 3, respectively" (Methods, Column density estimates); "using the typical ratio of $560 \pm 25$ in the ISM" (Results)
   - assumption: Optically thin emission, LTE, single excitation temperature shared by all water isotopologues, similar spatial distribution  
  > "As the spatial distribution of all three water isotopologues" (Results); "these water isotopologues emit from the same disk region" (Methods, Column density estimates)
   - fitting: _not stated_
   - validation: Optical depth, temperature, OPR, emitting-region and masing sensitivity tests (see step 8)  
  > "For the fiducial temperature of 199 K, the thermal linewidth and derived column densities of the upper energy levels, all lines analyzed in this work are optically thin." (Supplementary, Optical depth)
7. **Compare ratios with Class 0, comet 67P and collapsing-core models**: Compare D2O/H2O and (D2O/HDO)/(HDO/H2O) of V883 Ori with literature values for Class 0 objects and 67P, and with histograms of a collapsing-core chemical model classed as inheritance or reset  
  > "First of all, the water isotopologue ratios in the V883 Ori disk are compared to those in younger and older objects to look for similarity." (Supplementary, Water isotopologue ratios)
   - software: not stated
   - parameter: Inheritance: <~10% of ice destroyed; reset: >~70% destroyed  
  > "inheritance (all stream lines where $\lesssim 10$% of the water ice is destroyed) or reset (all stream lines where $\gtrsim 70$% of the water ice is destroyed)" (Discussion)
   - fitting: _not stated_
   - validation: V883 Ori point lies within 1 sigma of the peak of the inheritance model histogram  
  > "The V883 Ori datapoint coincides with the peak of the model prediction histogram for inheritance well within $1\sigma$" (Discussion)
8. **Test systematic uncertainties**: Vary excitation temperature by +/-100 K, estimate optical depth, test a smaller emitting annulus, test low OPR, discuss masking  
  > "by varying the temperature by $\pm 100$ K, the approximate range of temperatures found for COMs in this disk" (Supplementary, Excitation temperature)
   - software: not stated
   - parameter: Tex = 99, 199, 299 K; smallest emitting region an elliptical annulus 0.1-0.2 arcsec (area 5.3 times smaller); OPR = 1  
  > "the smallest physically motivated emitting region is an elliptical annulus between $0\ensuremath{\overset{\prime\prime}{.}}1$ and $0\ensuremath{\overset{\prime\prime}{.}}2$" (Supplementary, Optical depth); "If the OPR is at a low value of 1 for both molecules" (Supplementary, Ortho-to-para ratios)
   - fitting: _not stated_
   - validation: D2O/H2O stays consistent with inheritance in all variants tested  
  > "Therefore, even in this case the / ratio can be used to infer that water is inherited." (Supplementary, Optical depth)

## Software

- **CASA** 6.5.4: Self-calibration, continuum subtraction and imaging  
  > "The data were self-calibrated using CASA version 6.5.4" (Methods, Self-calibration)
- **tclean** : Imaging the D2O line and re-imaging HDO and H2-18-O (and mtmfs continuum model)  
  > "The line itself was imaged using the CASA task `tclean` with Briggs weighting" (Methods, Imaging)
- **ft** : Adding the continuum model to the measurement set  
  > "The resulting model for the continuum emission was added to the measurement set using `ft`" (Methods, Continuum subtraction)
- **uvsub** : Subtracting the continuum model from the visibilities  
  > "This model was then used to subtract the continuum using the CASA task `uvsub`." (Methods, Continuum subtraction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| D2O peak signal-to-noise ratio in shifted spectrum | 11 | not stated | dimensionless | 5 | The line is detected at a peak signal-to-noise ratio of 11 in the shifted spectrum |
| Peak S/N of continuum before and after phase self-calibration | 495 to 1457 | not stated | dimensionless | 1 | from a peak signal-to-noise ratio of 495 to one of 1457 |
| D2O line flux (Keplerian mask) | 53 | 4 | mJy km/s | 4 | $53 \pm 4$ / $61 \pm 4$ |
| D2O line flux (shifted spectrum) | 61 | 4 | mJy km/s | 5 | $53 \pm 4$ / $61 \pm 4$ |
| HDO 225 GHz line flux (Keplerian mask; shifted spectrum) | 358 ; 408 | 14 ; 12 | mJy km/s | 4 | $358 \pm 14$ / $408 \pm 12$ |
| H2-18-O 203 GHz line flux (Keplerian mask; shifted spectrum) | 43 ; 58 | 9 ; 10 | mJy km/s | 4 | $43 \pm 9$ / $58 \pm 10$ |
| N(D2O), N(HDO), N(H2-18-O) (Keplerian mask) | 4.2e13 ; 49.5e14 ; 23.7e14 | 1.2e13 ; 6.9e14 ; 5.7e14 | cm^-2 | 6 | $(4.2 \pm 1.2)\times 10^{13}$ cm$^{-2}$, $(49.5 \pm 6.9) \times 10^{14}$ cm$^{-2}$, and $(23.7 \pm 5.7) \times 10^{14}$ cm$^{-2}$ |
| Total N(H2-16-O) | 13.3e17 | 3.2e17 | cm^-2 | 6 | scaled to a total column density of $(13.3\pm 3.2) \times 10^{17}$ cm$^{-2}$ |
| D2O/H2O | 3.2e-5 | 1.0e-5 in text (Table 3 lists 1.2) | dimensionless | 6 | These column densities translate to / = $(3.2 \pm 1.0) \times 10^{-5}$ and (/HDO) / (HDO/) = $2.3 \pm 1.0$. |
| (D2O/HDO)/(HDO/H2O) | 2.3 | 1.0 | dimensionless | 6 | These column densities translate to / = $(3.2 \pm 1.0) \times 10^{-5}$ and (/HDO) / (HDO/) = $2.3 \pm 1.0$. |
| D2O/HDO | 8.5e-3 | 2.8e-3 | dimensionless | 6 | ratio of $(8.5 \pm 2.8) \times 10^{-3}$ in this disk |
| D2O/H2O, double ratio from the shifted-spectrum method (Table 3) | 2.7e-5 ; 2.8 | 1.0e-5 ; 1.1 | dimensionless | 6 | Shifted spectrum / $4.9 \pm 1.4$ / $56.4 \pm 7.7$ / $32.3 \pm 6.3$ / $2.7 \pm 1.0$ / $8.6 \pm 2.8$ / $2.8 \pm 1.1$ |
| HDO/H2O from reimaged HDO and H2-18-O | 3.7e-3 | 1.0e-3 | dimensionless | 6 | we derive the HDO/ ratio to be $(3.7 \pm 1.0)\times 10^{-3}$ |
| D2O/H2O and double ratio at Tex = 99 K | 1.3e-5 ; 1.4 | 0.8e-5 ; 0.9 | dimensionless | 8 | 99 / $(1.3 \pm 0.8)\times 10^{-5}$ / $1.4 \pm 0.9$ |
| HDO optical depth at Tex = 199 K (text value; Supplementary Table 6 lists 1.8e-1) | 0.14 | not stated | dimensionless | 8 | The HDO line has the highest optical depth at 0.14 |

## Qualitative findings

- Pristine water formed in the earliest star-formation phases is available in a protoplanetary disk  
  > "Our result demonstrates that pristine water that formed at the earliest phases of star and planet formation is available in protoplanetary disks" (Discussion, Summary)
- The outburst is not expected to alter the water deuteration outside the inner 1-3 au  
  > "the outburst only affects the water deuteration in the inner 1-3 au" (Discussion)
- Differential dust optical depth, if present, would drive measured ratios further toward inheritance  
  > "the measured ratios will be driven further into the regime consistent with inheritance" (Discussion)
- HDO/H2O alone does not distinguish inheritance from reset  
  > "thus that this ratio does not distinguish inheritance from reset" (Supplementary, HDO/H2O ratio)
- COM deuteration in this disk is lower than in the hot corino IRAS 16296 B and comet 67P, interpreted as some reprocessing of COMs  
  > "This lower level of deuteration in the V883 Ori disk has been interpreted as an indication for some reprocessing of COMs" (Discussion, Deuteration of complex organic molecules)

## Claim tuples

- H: Is the water ice in the V883 Ori disk inherited from the cloud or reset in the disk? | E: Detect D2O with ALMA Band 7 and measure D2O/H2O and (D2O/HDO)/(HDO/H2O) using Keplerian-mask fluxes and LTE column densities | R: D2O detected (S/N 11); D2O/H2O = (3.2 +/- 1.0)e-5; (D2O/HDO)/(HDO/H2O) = 2.3 +/- 1.0, similar to Class 0 objects and comet 67P | F: The ice in the V883 Ori disk is inherited from the cold molecular cloud | **supported**
- H: Do the observed ratios match chemical-model predictions for inheritance rather than reset? | E: Overlay observed D2O/H2O on model histograms of a collapsing core | R: The V883 Ori data point lies within 1 sigma of the peak of the inheritance histogram | F: Models support inheritance | **supported**
- H: Is the double ratio (D2O/HDO)/(HDO/H2O) of the disk consistent with the inheritance model value? | E: Compare observed ratio with the model prediction of 10 and with the reset value ~5e-2 | R: Observed ratio is a factor of ~40-140 above the reset value but up to a factor of ~5 below the model inheritance value of 10 | F: Ratio is consistent with inheritance once variations in initial conditions are allowed (0.8-19) | **partially**
- H: Does the inheritance conclusion survive the main systematic uncertainties? | E: Vary excitation temperature, optical depth, emitting area, OPR and consider masing | R: D2O/H2O remains consistent with inheritance even at 99 K, with OPR = 1 and for a small emitting annulus; the double ratio is less robust (HDO optically thick in the small region, possible HDO masing) | F: The D2O/H2O ratio is the robust indicator | **supported**

## Reasoning

- Why this data: D2O is the most sensitive tracer of inheritance versus reset and had not been observed in the protoplanetary disk stage  
  > "is the most sensitive tool to distinguish inheritance from reset because it cannot reform efficiently after reprocessing" (Introduction); "In particular, observations of doubly deuterated water are missing in the protoplanetary disk stage." (Introduction)
- Why this method: Lines are blended with COM emission, so Keplerian masking and spectral shifting are used; uvcontsub was impractical because of the line density; robust = 0 balances resolution and noise  
  > "Keplerian masking in the channel maps and spectral shifting of the spectrum" (Methods, Flux measurements); "too few line-free channels were available to subtract the continuum emission in the $uv$-plane using the standard CASA task `uvcontsub`" (Methods, Continuum subtraction); "which provides the best balance between spatial resolution and noise" (Methods, Imaging)
- Alternative: HDO 241 GHz line rejected (too blended)  
  > "The HDO 241 GHz line on the other hand is too severely blended and is therefore not considered in this analysis." (Methods, Flux measurements)
- Alternative: Shifted-spectrum fluxes not used as fiducial; Keplerian-mask fluxes used for the final analysis  
  > "the fluxes measured using the Keplerian masks are used for the final analysis presented in the main text" (Methods, Flux measurements)
- Alternative: Smaller-region H2-18-O spectrum not used in calculations to avoid bias  
  > "This spectrum is not used for any of calculations to avoid a bias" (Methods, Flux measurements)
- How they decided it was enough: Cleaning continued to 1 sigma to capture all flux  
  > "The image is cleaned down to $1\sigma$ to capture all the flux in the model and make the final measurement independent of any non-Gaussian features in the beam" (Methods, Imaging)
- Limitation (authors): Excitation temperature taken from two HDO lines, one heavily blended, so somewhat uncertain; only a single line per isotopologue  
  > "the derived excitation temperature is somewhat uncertain" (Supplementary, Excitation temperature); "As only a single line of each water isotopologue is analyzed in this work" (Supplementary, Excitation temperature)
- Limitation (authors): HDO and H2-18-O may be weakly masing, which would make the double ratio not meaningful  
  > "the HDO 225 GHz and the H$_2^{18}$O lines are possibly weakly masing in a large region in the V883 Ori disk" (Supplementary, Masing)
- Limitation (authors): Line-flux uncertainties exclude absolute flux calibration uncertainty  
  > "The reported uncertainties on the line fluxes do include the statistical uncertainty but not the 5% absolute flux calibration uncertainty" (Methods, Flux measurements)
- Caveat (inferred, ours): Single-temperature LTE with an assumed 0.4 arcsec emitting ellipse; ratios depend on the shared Tex taken from a partly blended HDO pair
- Caveat (inferred, ours): Text and tables disagree in places (D2O/H2O error 1.0 vs 1.2; HDO optical depth 0.14 vs 0.18)
- Caveat (inferred, ours): The observed double ratio (2.3) sits below the model inheritance value (10); one model family is the only reset/inheritance benchmark
- Caveat (inferred, ours): COM-deblending uses mirrored line templates and hand-chosen mask convolution, which are not objective

## Reproducibility

- Data public (paper): Both ALMA programs stated to be public in the ALMA archive  
  > "are publicly available on the ALMA archive" (Data availability)
- Products in archive: _not stated_
- Code: Code available on request; based on public python packages  
  > "In addition, the code itself is available upon reasonable request to M.L." (Code availability)
- Missing: Keplerian-mask and spectral-shifting code and package names
- Missing: Clean parameters (image size, cell, niter, thresholds) and line-free channel lists
- Missing: Calibration and imaging details for the 2021.1.00186.S HDO and H2-18-O data
- Missing: Partition-function values at 199 K
- Data volume (inferred): Roughly 50-150 GB for three Band 7 EBs with high spectral resolution plus the earlier HDO and H2-18-O datasets
- Score (inferred): 3/5, Public data, specified self-calibration, imaging and flux-measurement recipe with numeric results, but mask package, clean settings and code are not given
- Rediscovery candidate: no, Data are public and results are numeric, but key imaging parameters, line-free channels and the deblending code are missing, so the recipe cannot be redone as stated

## Links

- Method: exoALMA large program self-calibration (citation not preserved in text) (Self-calibration procedure followed in this work)
- Companion: Tobin et al. 2023 (cite: Tobin2023) (Earlier HDO and H2-18-O observations of the V883 Ori disk (2021.1.00186.S), reimaged here)
- Related: 2021.1.00186.S
- Related: 2023.1.00588.S
- Related: exoALMA

## Checks

```json
{
 "quotes": 147,
 "quotes_ok": 147,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 15,
 "numeric_problems": 0,
 "fill": {
  "facts": 113,
  "stated": 83,
  "rate": 0.735
 },
 "evidence_ok": true
}
```
