# The Ophiuchus DIsc Survey Employing ALMA (ODISEA) - I: project description and continuum images at 28 au resolution

`2019MNRAS.482..698C` | Monthly Notices of the Royal Astronomical Society 2019 | first author: Cieza, Lucas A. | arXiv: 1809.08844 | DOI: 10.1093/mnras/sty2653

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: protoplanetary_disks, star_formation
- Question: What are the 1.3 mm continuum fluxes, sizes, substructures and implied dust masses of the Spitzer-selected (Sample A) discs in Ophiuchus at 0.2'' resolution?  
  > "Here we present 1.3 mm/230 GHz continuum images of 147 targets at 0.2$''$ (28 au) resolution and a typical rms of 0.15 mJy." (abstract)
- Target **Ophiuchus Molecular Cloud Sample A (147 Class I/Flat/faint-limit Class II YSOs)**: coordinates per-target coordinates in Table 1 (not summarized)  
  > "At a distance of 140 $\pm$ 10 pc (Ortiz-Leon et al. 2017, Canovas et al. in prep.), Ophiuchus is the closest star-forming region with at least $\sim$300 discs." (2.1 Sample Selection); z/distance 140 ± 10 pc  
  > "At a distance of 140 $\pm$ 10 pc (Ortiz-Leon et al. 2017, Canovas et al. in prep.), Ophiuchus is the closest star-forming region with at least $\sim$300 discs." (2.1 Sample Selection); distance from Ortiz-Leon et al. 2017, Canovas et al. in prep.  
  > "At a distance of 140 $\pm$ 10 pc (Ortiz-Leon et al. 2017, Canovas et al. in prep.), Ophiuchus is the closest star-forming region with at least $\sim$300 discs." (2.1 Sample Selection)

## Data provenance

- ALMA projects: 2016.1.00545.S
- bands: Band 6 (230 GHz/1.3 mm)  
  > "here we present Band-6 (230 GHz/1.3 mm) continuum observations of 147 discs in the Ophiuchus Molecular Cloud" (1 Introduction)
- frequencies and spectral setup: Three line SPWs at 230.538, 220.398684, 219.560358 GHz (0.08 km/s resolution; 117, 58.6, 58.6 MHz); two continuum SPWs at 233.00 and 218.00 GHz, 1.875 GHz each  
  > "Two additional spectral windows, centered at 233.00 and 218.00 GHz, had 1.875 GHz bandwidths and were selected for continuum observations, for a total continuum bandwidth of 3.98 GHz." (2.3 Observations and data reduction)
- continuum bandwidth: 3.98 GHz  
  > "for a total continuum bandwidth of 3.98 GHz." (2.3 Observations and data reduction)
- arrays: 12-m array, 42-45 antennas  
  > "42-45 of the 12-m ALMA antennas were used with baselines ranging from 17 to 2647 m." (2.3 Observations and data reduction)
- configurations: C40-5  
  > "The nominal array configuration was C40-5" (2.3 Observations and data reduction)
- baselines: 17 to 2647 m  
  > "baselines ranging from 17 to 2647 m." (2.3 Observations and data reduction)
- angular resolution: 0.28'' x 0.19'' synthesized beam (~0.2'', 28 au)  
  > "a synthesized beam of 0.28$''$ $\times$ 0.19$''$." (2.3 Observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: typical rms ~0.15 mJy/beam  
  > "we obtained a typical rms of $\sim$0.15 mJy beam$^{-1}$" (2.3 Observations and data reduction)
- time on source: _not stated_
- observing dates: 3 executions between July 13th and 14th 2017  
  > "on a single scheduling block, which was executed 3 times between July 13th and 14th 2017" (2.3 Observations and data reduction)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (SPW centered 230.538 GHz)
- Line: 13CO J=2-1 (SPW centered 220.398684 GHz)
- Line: C18O J=2-1 (SPW centered 219.560358 GHz)
- Other facility **Spitzer Cores to Discs Legacy Program**: Parent catalog of 297 YSOs and IR photometry used for sample selection  
  > "The ODISEA sample is the full catalog of 297 Young Stellar Objects (YSOs) in Ophiuchus from the *“Cores to Discs” Spitzer* Legacy Program (Evans et al. 2009b)." (2.1 Sample Selection)
- Other facility **Gaia DR2**: Proper motions used to explain position offsets  
  > "which we attribute to the proper motions of the targets based on the results of the Gaia Data Release 2 (Gaia Collaboration et al. 2018)." (3.1 Continuum images, disc photometry, and sizes)
- External data: Spitzer catalog, 2MASS and Spitzer photometry of the 147 targets  
  > "Table [\[table:c2d\]](#table:c2d) shows the 2MASS and *Spitzer* photometry from these 147 objects, taken from the NASA/IPAC Infrared Science Archive." (2.1 Sample Selection) [from Evans et al. 2009b (Cores to Discs)]
- External data: Spectral types and companion separations from literature  
  > "We have also collected spectral types from the literature for 88 objects from our sample." (3.3 General trends) [from Cieza et al. 2010; Erickson et al. 2011; Wilking et al. 2005; Manara et al. 2015; McClure et al. 2010 and others]
- External data: Dust masses of other regions for comparison (Lupus, Upper Sco, Cha I, sigma Ori, IC 348, Taurus)  
  > "For comparison, we perform the same analysis for objects in Lupus (Ansdell et al. 2016), Upper Scorpius (Barenfeld et al. 2016), Chamaeleon I (Pascucci et al. 2016)" (4.2 Comparison to other regions) [from Ansdell et al. 2016; Barenfeld et al. 2016; Pascucci et al. 2016; Ansdell et al. 2017; Ruiz-Rodriguez et al. 2018; Andrews et al. 2013]

## Processing

### Calibration

- pipeline or manual: Calibrated by the ALMA observatory with standard calibration  
  > "All data were calibrated using the Common Astronomy Software Applications package (CASA v4.4; McMullin et al. 2007) by the ALMA observatory." (2.3 Observations and data reduction)
- casa version: CASA v4.4  
  > "(CASA v4.4; McMullin et al. 2007)" (2.3 Observations and data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1517-2422 and J1733-1304  
  > "The objects J1517-2422 and J1733-1304 were observed as flux calibrators" (2.3 Observations and data reduction)
- flux scale uncertainty: 10% calibration uncertainty; epochs agree within <10%, no rescaling  
  > "The flux calibration in the three epochs agreed within $<$10$\%$ and thus no rescaling of the flux was applied." (2.3 Observations and data reduction)
- self calibration: Phase-only self-calibration for ~50 sources with flux >~15 mJy  
  > "For the subset of $\sim$50 sources with fluxes $\gtrsim$ 15 mJy, we perform phase-only self-calibration" (3.4 Disc substructures)

### Imaging

- task: CLEAN  
  > "We used the CLEAN algorithm to image the data adopting Briggs weights and robust parameter equal to zero" (2.3 Observations and data reduction)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0 (uniform weighting for substructure images)  
  > "adopting Briggs weights and robust parameter equal to zero as a balance between resolution and sensitivity." (2.3 Observations and data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Three nights concatenated and processed together  
  > "The observations from all three nights were concatenated and processed together to increase the signal to noise and *uv*-coverage." (2.3 Observations and data reduction)
- smoothing: _not stated_
- final beam: 0.28'' x 0.19'' (≈0.15'' with uniform weighting)  
  > "a synthesized beam of 0.28$''$ $\times$ 0.19$''$." (2.3 Observations and data reduction)
- final rms: ~0.15 mJy/beam  
  > "we obtained a typical rms of $\sim$0.15 mJy beam$^{-1}$" (2.3 Observations and data reduction)

### Inherited from earlier work

- Kaplan-Meier survival analysis for dust-mass distributions including upper limits  
  > "calculated using the Kaplan-Meier estimator in the ASURV package (Lavalley et al. 1992) to include upper limits, as described by Ansdell et al. (2016)." (4.2 Comparison to other regions) [from Ansdell et al. (2016)]
- Dust opacity prescription kappa = 0.1 (nu/1e12 Hz)^beta cm2/g  
  > "Adopting the prescription for $\kappa_\nu$ at millimeter wavelengths from Beckwith et al. (1990)," (4.1 Disc dust masses and sizes) [from Beckwith et al. (1990)]
- Dust temperature 20 K (median disc temperature in Taurus)  
  > "$T_{\rm dust}$ = 20 K, which is the median disc temperature in Taurus calculated by Andrews $\&$ Williams (2005)" (4.1 Disc dust masses and sizes) [from Andrews & Williams (2005)]

### Not stated but needed to reproduce (our reading)

- CLEAN parameters: cell size, image size, masks, threshold, deconvolver, number of iterations
- Continuum channel selection / flagging of line-contaminated channels
- Self-calibration solution intervals and reference models
- Exact deprojection and radial-profile binning procedure
- Individual aperture sizes for flux in non-substructure sources and starting guesses for uvmodelfit
- Stacking implementation details (pixel grid, primary-beam handling)
- Exact CASA/pipeline version of the delivered calibration

## Analysis recipe

1. **Detect sources and measure peak/rms**: Inspect images with CASA Viewer; imstat peak within 1'' aperture and rms in 1.0-1.2'' annulus  
  > "We first used the *imstat* task to search for the peak flux value within an aperture of 1$''$ in radius and calculated an rms from an annulus with an inner and outer radius of 1.0$''$ and 1.2$''$." (3.1 Continuum images, disc photometry, and sizes)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit fluxes and sizes of single sources in the uv plane**: uvmodelfit point source and Gaussian fits for single objects with peak S/N>5; resolved only if S/N>30 and Gaussian flux > point flux + 3 rms; elliptical disc model for substructured sources  
  > "we provide size information only if the source has a peak S/N $>$ 30 and the Gaussian flux is greater than the point source flux plus 3 times the rms of the sky between 1 and 1.2$''$ of the target." (3.1 Continuum images, disc photometry, and sizes)
   - software: CASA uvmodelfit
   - parameter: Free parameters: flux, major/minor FWHM, PA, offsets <1''  
  > "the integrated flux density, the Full Width at Half Maximum (FWHM) along the major and minor axis, the Position Angle (PA), and small offsets ($<$ 1.0$"$) in right ascension and declination from the phase center." (3.1 Continuum images, disc photometry, and sizes)
   - fitting: uvmodelfit; size uncertainties likely underestimated  
  > "the *uvmodelfit* documentation indicates that the size uncertainties are likely to be underestimated by this task." (3.1 Continuum images, disc photometry, and sizes)
   - validation: _not stated_
3. **Photometry of multiples and substructured discs, and non-detections**: CASA Viewer 2-D image-plane fitting for multiples and ~3'' apertures for substructured discs; point-source uvmodelfit at offset-corrected positions (-0.08'', -0.56'') for non-detections  
  > "Because the mean displacement is larger than the beam, we apply the observed offsets to the nominal position of the non-detected targets before fitting a point source at the new location." (3.1 Continuum images, disc photometry, and sizes)
   - software: CASA Viewer, CASA uvmodelfit
   - fitting: _not stated_
   - validation: Offsets compared with expected proper-motion shift (~0.1'' RA, ~0.5'' Dec)  
  > "This should translate to a shift in coordinates of $\sim$0.1$''$ and $\sim$0.5$''$ in RA and Dec, respectively, consistent with the observed offsets." (3.1 Continuum images, disc photometry, and sizes)
4. **Stack non-detections**: Mean of each pixel from the images of the 27 non-detections centered at nominal positions  
  > "we stack the images of the 27 non-detections, calculating the mean of each pixel from the individual images centered at the nominal location of each target." (3.2 Stacking of non-detections)
   - fitting: _not stated_
   - validation: Stack offset of -0.5'' matches mean RA offset of detections  
  > "This offset is very consistent with the mean offset in RA found for the detected discs (-0.56$''$)" (3.2 Stacking of non-detections)
5. **Search for substructure**: Phase-only self-calibration and uniform-weight imaging for ~50 sources >~15 mJy; visual inspection; deprojected radial profiles using fitted PA and axes  
  > "we use the coordinates, position angles and FWHM values of the major and minor axes listed in Table [\[table:results\]](#table:results) to deproject the images and plot the deprojected radial profiles." (3.4 Disc substructures)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
6. **Convert flux to dust mass and compare regions**: Optically thin M_dust = F d^2/(kappa B(T)); Kaplan-Meier cumulative distributions with ASURV  
  > "M_{dust}  = 0.58 \times \frac{F_{1.3mm}}{\mathrm{mJy}}  M_{\oplus}" (4.1 Disc dust masses and sizes)
   - software: ASURV
   - parameter: kappa_1.3mm = 0.023 cm2/g (beta=1), d = 140 pc, T_dust = 20 K  
  > "we obtain $\kappa_{1.3mm}$ = 0.023 cm$^2$ g$^{-1}$ for $\beta$ = 1.0." (4.1 Disc dust masses and sizes)
   - assumption: Optically thin emission, T=20 K, beta=1, Beckwith opacity, 140 pc  
  > "Since protoplanetary discs typically become optically thin at millimeter wavelengths outside the first few au" (4.1 Disc dust masses and sizes)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** v4.4: Calibration (by observatory), imaging, Viewer inspection, imstat, uvmodelfit, 2-D fitting  
  > "All data were calibrated using the Common Astronomy Software Applications package (CASA v4.4; McMullin et al. 2007) by the ALMA observatory." (2.3 Observations and data reduction)
- **ASURV** : Kaplan-Meier estimator for dust mass distributions with upper limits  
  > "calculated using the Kaplan-Meier estimator in the ASURV package (Lavalley et al. 1992) to include upper limits" (4.2 Comparison to other regions)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Discs detected | 133 (in 120 systems) | not stated | discs | 2 | We detect a total of 133 discs in 120 systems. |
| Spatially resolved discs | 53 | not stated | discs | 2 | Fifty-three of these discs are spatially resolved. |
| Stacked non-detection flux | 0.16 | rms 0.04 mJy | mJy | 4 | The stacked image has an rms of 0.04 mJy and shows a 4-$\sigma$ (0.16 mJy) detection |
| Dust mass of stacked non-detections | 0.09 | not stated | Earth masses | 6 | corresponds to an average dust mass of just 0.09 M$_{\oplus}$. |
| Flux-to-mass conversion | 0.58 | not stated | Earth masses per mJy | 6 | M_{dust}  = 0.58 \times \frac{F_{1.3mm}}{\mathrm{mJy}}  M_{\oplus} |
| Discs with clear substructure | 8 (plus 4 with hints) | not stated | discs | 5 | We find clear substructures (inner cavities, rings, gaps, and/or spiral arms) in 8 of the sources and hints of such structures in another 4 discs. |
| Discs with dust mass sufficient for 10 Earth-mass core | ~50 (~1/3) | not stated | discs | 6 | only $\sim$50 targets (1/3 of the sample) have enough dust to form a critical-mass rocky core |

## Qualitative findings

- Dust mass distribution in Ophiuchus is similar to other young (1-2 Myr) regions such as Taurus and Lupus  
  > "We find that the dust mass distribution in our Ophiuchus sample (which is not yet complete) is very similar to those of other young regions (1-2 Myr) as Taurus and Lupus." (4.2 Comparison to other regions)
- Brighter discs tend to be larger but with ~factor 10 dispersion; discs with close companions tend to be small  
  > "There is a tendency for brighter discs to be larger, but the flux vs size relation show a significant dispersion (a factor of $\sim$10)." (3.3 General trends)

## Claim tuples

- H: Do Ophiuchus discs have enough dust mass to form planets? | E: Convert 1.3 mm fluxes to dust masses with standard assumptions | R: All detected discs have M_dust >~0.5 Earth masses; only ~50 have ~10 Earth masses | F: All detected discs can form rocky planets; only ~1/3 can form gas-giant cores | **supported**
- H: Are substructures common among bright discs? | E: Self-calibrated uniform-weight images and deprojected radial profiles | R: 8 clear and 4 possible substructures, all among the brightest sources | F: ~28% (7/25) of the brightest, and up to ~50% of >50 mJy sources may show substructure | **partially**
- H: What is the typical disc size and brightness distribution? | E: Fit sizes of resolved sources, set unresolved at FWHM 0.2'' | R: Most discs radii <15 au; ~15% have >30 au | F: Disc population is dominated by compact, faint discs | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Ad hoc resolved criterion used because uvmodelfit size uncertainties are underestimated  
  > "Therefore, we use *ad hoc* criteria to decide whether the source is spatially resolved" (3.1 Continuum images, disc photometry, and sizes)
- How they decided it was enough: _not stated_
- Limitation (authors): Fluxes should be taken with caution because of mixed photometry methods; 10% calibration uncertainty  
  > "we emphasize that the fluxes should be taken with caution, especially for objects with clear substructures." (3.1 Continuum images, disc photometry, and sizes)
- Limitation (authors): Dust masses may be underestimated (optically thick) or overestimated (higher temperature)  
  > "the optically thin assumption breaks down in the dense inner regions" (4.1 Disc dust masses and sizes)
- Limitation (authors): Sample B not observed successfully; sample incomplete  
  > "the observations for Sample B were not successful due to an scripting problem at the observatory" (2.1 Sample Selection)
- Caveat (inferred, ours): Single dust temperature of 20 K regardless of stellar luminosity biases masses for compact bright discs
- Caveat (inferred, ours): Gaussian FWHM size definition is non-standard and not equal to outer radius
- Caveat (inferred, ours): Ad hoc resolved criterion (S/N>30) leaves many sources unresolved
- Caveat (inferred, ours): Quoted counts differ across text (23 vs 22 discs >30 au)

## Reproducibility

- Data public (paper): Data cited by project code; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA #2016.1.00545.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: CLEAN parameters (cell, image size, masks, thresholds)
- Missing: Self-calibration details
- Missing: Full results tables only online
- Missing: Deprojection and profile details
- Data volume (inferred): ~100-300 GB raw for one scheduling block with 3 executions (guess)
- Score (inferred): 3/5, Single public project with clear photometry recipe and numeric tables, but imaging parameters missing.
- Rediscovery candidate: yes, Single ALMA project; recipe for photometry and mass conversion is clear and results are numeric.

## Links

- Method: Beckwith et al. 1990 (dust opacity prescription)
- Method: Ansdell et al. 2016 (Kaplan-Meier treatment of upper limits)
- Companion: Williams et al. in preparation (gas content from CO isotopologues)
- Companion: Perez et al. in preparation (radiative transfer modeling)
- Companion: Ruiz-Rodriguez et al. in preparation (disc properties vs stellar mass and age)
- Companion: Zurlo et al. in preparation (effects of companions)
- Related: Cox et al. 2017 Ophiuchus ALMA survey
- Related: Lupus ALMA survey (Ansdell et al.)
- Related: Upper Scorpius survey (Barenfeld et al.)

## Checks

```json
{
 "quotes": 67,
 "quotes_ok": 67,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 79,
  "stated": 52,
  "rate": 0.658
 },
 "evidence_ok": true
}
```
