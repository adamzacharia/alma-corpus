# Continuum and spectral-line observations of the OH megamaser galaxy IRAS 01298‒0744

`2024A&A...687A.193W` | Astronomy and Astrophysics 2024 | first author: Wu, Zhongzu | arXiv: - | DOI: 10.1051/0004-6361/202450206

Card schema 1.0 | model gemini-4-argon | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: Investigate the high-resolution properties of OH line and radio continuum emission from IRAS 01298−0744 and their relationship with the nuclear region's environment, merging phase, radio AGN, dense gas, and possible low-velocity outflows.  
  > "The primary objective of this paper is to investigate the high-resolution properties of OH line and radio continuum emission from IRAS 01298−0744, and better understand the relationship between OHM emission and the nuclear region’s environment" (1. Introduction)
- Target **IRAS 01298−0744**: coordinates RA: 01 32 21.415, Dec: −07 29 08.347  
  > "The optical redshift of IRAS 01298−0744 is 0.1362 (Soto & Martin 2012)." (1. Introduction); "centred at RA:01 32 21.415 Dec:−07 29 08.347" (Figure 1 caption); z/distance z = 0.1362  
  > "The optical redshift of IRAS 01298−0744 is 0.1362 (Soto & Martin 2012)." (1. Introduction); "centred at RA:01 32 21.415 Dec:−07 29 08.347" (Figure 1 caption); distance from Soto & Martin 2012  
  > "The optical redshift of IRAS 01298−0744 is 0.1362 (Soto & Martin 2012)." (1. Introduction); "centred at RA:01 32 21.415 Dec:−07 29 08.347" (Figure 1 caption)

## Data provenance

- ALMA projects: 2017.1.00057.S
- bands: _not stated_
- frequencies and spectral setup: 233.1–237.9 GHz, channel width 14.2 km s−1 (binned to 14 km s−1)  
  > "2017Dec.10 233.1–237.9 HCN(3–2) ALMA J0141−0928 2017.1.00057.S 14.2 150 × 120 −55 0.53" (Table 1); "we initially restored the data calibrated by the pipeline and binned the channels to 14 km s−1 using the CASA package." (2. Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 150 × 120 mas (PA −55 deg)  
  > "2017Dec.10 233.1–237.9 HCN(3–2) ALMA J0141−0928 2017.1.00057.S 14.2 150 × 120 −55 0.53" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: 0.53 mJy beam−1 (HCN), 0.47 mJy beam−1 (HCO+), 0.032 mJy beam−1 (Continuum)  
  > "2017Dec.10 233.1–237.9 HCN(3–2) ALMA J0141−0928 2017.1.00057.S 14.2 150 × 120 −55 0.53" (Table 1); "... . . . HCO+(3–2) . . . . . . . . . . . . . . . . . . 0.47" (Table 1); "... . . . Continuum . . . . . . . . . – . . . . . . 0.032" (Table 1)
- time on source: _not stated_
- observing dates: 2017 Dec. 10  
  > "2017Dec.10 233.1–237.9 HCN(3–2) ALMA J0141−0928 2017.1.00057.S 14.2 150 × 120 −55 0.53" (Table 1)
- pi or archival as stated: archival, PI M. Imanishi  
  > "from the archival Atacama Large Millimeter Array (ALMA) project 2017.1.00057.S (PI M. Imanishi)." (2. Observations and data reduction)
- Line: HCN 3–2 (not stated)
- Line: HCO+ 3–2 (not stated)
- Other facility **VLBA**: L-band continuum and OH 1667 MHz line observations (program BW144), and archival S- and X-band continuum observations (program BH237D).  
  > "We conducted continuum and OH line observations of IRAS 01298−0744 using the Very Long Baseline Array (VLBA) for eight hours on August 2, 2022." (2. Observations and data reduction); "We also tried to find compact radio-continuum emission from the archival VLBA project BH237D (see Table 1)." (4.4. The nature of the continuum emission and association of the OH line)
- Other facility **SDSS**: Optical R-band image.  
  > "We overlaid the OH emission onto an optical R-band Sloan Digital Sky Survey (SDSS) image" (3. Results)
- Other facility **VLASS**: Radio continuum emission contours.  
  > "Left panel: blue contours indicate the Very Large Array Sky Survey (VLASS, Lacy et al. 2020) continuum emission" (Figure 3 caption)
- External data: Single-dish GBT OH line profile  
  > "The OH line profile obtained from GBT observations by Willett (2012) is represented by the solid line." (Figure 1 caption) [from Willett (2012)]
- External data: Normalised Na I D spectra  
  > "The normalised Na I D spectra from Rupke et al. (2005) are represented by the black dotted line in the right panel." (Figure 1 caption) [from Rupke et al. (2005)]
- External data: HCN and HCO+ line FWHMs and velocity maps  
  > "HCN and HCO+ line emissions from IRAS 01298−0744 have been detected by Imanishi et al. (2019). The full widths at half-maximum (FWHMs) of the two lines are 621 and 634 km s−1, respectively" (4.2. Comparing OH with sub-millimetre line emission) [from Imanishi et al. (2019)]

## Processing

### Calibration

- pipeline or manual: pipeline restored  
  > "we initially restored the data calibrated by the pipeline and binned the channels to 14 km s−1 using the CASA package." (2. Observations and data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: primary-beam-corrected continuum image used from archive  
  > "For our examination of the sub-millimetre radio-continuum emission, we utilised the primary-beam-corrected image file of Project 2017.1.00057.S, which is readily accessible in the ALMA archive." (2. Observations and data reduction)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs weighting with robust = 0.5  
  > "These data were reimaged following the parameters outlined by Imanishi et al. (2019), specifically employing Briggs weighting with robust = 0.5 and gain = 0.1 settings." (2. Observations and data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: primary-beam-corrected continuum image used  
  > "For our examination of the sub-millimetre radio-continuum emission, we utilised the primary-beam-corrected image file of Project 2017.1.00057.S, which is readily accessible in the ALMA archive." (2. Observations and data reduction)
- array combination: _not stated_
- smoothing: ALMA HCN and HCO+ spectra smoothed to 45 km s−1; VLBA OH spectrum smoothed to about 20 km s−1  
  > "The HCN line profiles obtained from ALMA observations (project: 2017.1.00057.S) are depicted by the dashed black line, which was generated in a circular region (radius ∼150 mas) and has been smoothed to 45 km s−1." (Figure 1 caption)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- ALMA line reimaging parameters (Briggs weighting with robust = 0.5 and gain = 0.1)  
  > "These data were reimaged following the parameters outlined by Imanishi et al. (2019), specifically employing Briggs weighting with robust = 0.5 and gain = 0.1 settings." (2. Observations and data reduction) [from Imanishi et al. (2019)]

### Not stated but needed to reproduce (our reading)

- CASA version used for ALMA pipeline restoration and reimaging
- Continuum subtraction procedure for ALMA HCN and HCO+ spectral cubes
- Stopping threshold and masking during ALMA line cube cleaning

## Analysis recipe

1. **Calibrate and image VLBA OH and radio continuum data**: Calibrate VLBA data in AIPS, image continuum and spectral line in DIFMAP, subtract continuum using CLEANed continuum map, and extract integrated OH profile over a 50x50 mas region.  
  > "To calibrate the VLBA data, we utilised the NRAO Astronomical Image Processing System (AIPS) package." (2. Observations and data reduction); "The calibrated data were imported into the DIFMAP package (Shepherd 1997) to generate continuum- and spectral-line images." (2. Observations and data reduction); "We generated the OH line profiles by integrating the flux densities over an area of approximately 50 mas squared in each channel image (see Figs. 1 and 2)." (3. Results)
   - software: AIPS, DIFMAP
   - parameter: integration area ~ 50 x 50 mas, channel width 3.8 km s−1  
  > "extracted from a square region measuring about 50 × 50 mas and centred at RA:01 32 21.415 Dec:−07 29 08.347" (Figure 1 caption); "2022Aug.02 1.5 OH VLBA J0127−0821 BW144 3.8 12.4 × 5.1 −0.3 1.9" (Table 1)
   - assumption: Heliocentric velocity with optical definition; H0 = 73 km s−1 Mpc−1, Omega_M = 0.27, Omega_Lambda = 0.73  
  > "At the distance of this galaxy, 1 mas corresponds to approximately 2.3 pc, assuming H0 = 73 km s−1 Mpc−1, ΩM = 0.27, and ΩΛ = 0.73." (1. Introduction); "We also set the velocity using the heliocentric system with the optical definition for velocity." (2. Observations and data reduction)
   - fitting: Direct fit of calibrated continuum visibilities with an elliptical Gaussian model, plus image-plane Gaussian fitting for compact OH components A-D.  
  > "We employed Gaussian fitting for these components and determined that their sizes are smaller than the beam FWHM, as summarised in Table 1." (3. Results); "To measure the total continuum emission, we performed a direct fit of calibrated visibilities using an elliptical" (3. Results)
   - validation: Compared integrated VLBA OH spectrum with GBT single-dish spectrum; compared visibility fit of continuum flux with 50 mas image integration.  
  > "Moreover, the VLBA observation captures over 82% of the integrated flux densities across the velocity ranges presented in the single-dish GBT profile (see Fig. 1)." (3. Results); "After obtaining the clean image, we further integrated over a 50 mas region to determine the radio-continuum flux. Both techniques provided a flux density close to 2 mJy." (3. Results)
2. **Fit OH spectral line components and map velocity structure**: Extract spectra at each pixel across a 50 mas region and fit single or multiple Gaussian components to line profiles at components A, B, C, D, and positions OH1-8.  
  > "Additionally, we utilised the ‘Spectral Profile’ tool in the Common Astronomy Software Application package (CASA; McMullin et al. 2007) to generate and fit OH line profiles at selected pixels." (2. Observations and data reduction); "We performed line profile fitting for the four primary components (A, B, C, and D), as well as for OH5, which exhibited multiple components." (3. Results)
   - software: CASA
   - parameter: Square region 50 mas in size  
  > "Additionally, we selected a square region measuring 50 mas in size to encompass the broader OH emission." (3. Results)
   - fitting: Single and multi-Gaussian spectral line profile fitting.  
  > "The OH line profiles are fitted with two or more Gaussian components" (Figure 5 caption); "For OH1-8, with the exception of OH5, we used single-peak fitting, and the results are outlined in Table A.1." (3. Results)
   - validation: Plotted residual spectra (data - model) in Fig. 5.  
  > "the upper spectrum of each panel shows the residual spectrum (data-model), which are plotted with an offset (+44 mJy) for clarity." (Figure 5 caption)
3. **Restore, reimage, and extract ALMA HCN, HCO+, and continuum data for comparison**: Restore pipeline-calibrated ALMA data, bin channels to 14 km s−1, reimage HCN and HCO+ lines, extract spectra from a 150 mas radius circular region smoothed to 45 km s−1, and compare spatially and kinematically with VLBA OH and continuum.  
  > "To analyse the data of the sub-millimetre HCN and HCO+ lines, we initially restored the data calibrated by the pipeline and binned the channels to 14 km s−1 using the CASA package." (2. Observations and data reduction); "The HCN line profiles obtained from ALMA observations (project: 2017.1.00057.S) are depicted by the dashed black line, which was generated in a circular region (radius ∼150 mas) and has been smoothed to 45 km s−1." (Figure 1 caption)
   - software: CASA
   - parameter: robust = 0.5, gain = 0.1, extraction radius ~ 150 mas, smoothed to 45 km s−1  
  > "specifically employing Briggs weighting with robust = 0.5 and gain = 0.1 settings." (2. Observations and data reduction); "generated in a circular region (radius ∼150 mas) and has been smoothed to 45 km s−1." (Figure 1 caption)
   - fitting: _not stated_
   - validation: Checked consistency of peak velocity, line width, and emission regions with Imanishi et al. (2019).  
  > "The two sub-millimetre emission lines exhibited similar properties, including the peak velocity, line width, and emission regions, which were consistent with the results reported by Imanishi et al. (2019)." (2. Observations and data reduction)

## Software

- **AIPS** : Calibration of VLBA data  
  > "To calibrate the VLBA data, we utilised the NRAO Astronomical Image Processing System (AIPS) package." (2. Observations and data reduction)
- **DIFMAP** : Generating VLBA continuum and spectral-line images  
  > "The calibrated data were imported into the DIFMAP package (Shepherd 1997) to generate continuum- and spectral-line images." (2. Observations and data reduction)
- **CASA** : Generating and fitting OH line profiles with Spectral Profile tool; restoring, binning, and reimaging ALMA HCN and HCO+ data  
  > "Additionally, we utilised the ‘Spectral Profile’ tool in the Common Astronomy Software Application package (CASA; McMullin et al. 2007) to generate and fit OH line profiles at selected pixels." (2. Observations and data reduction); "we initially restored the data calibrated by the pipeline and binned the channels to 14 km s−1 using the CASA package." (2. Observations and data reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Recovered fraction of single-dish OH line emission | 82 | not stated | % | 1 | We recover over 82% of the OH line emission seen in single-dish observations; Moreover, the VLBA observation captures over 82% of the integrated flux densities across the velocity ranges presented in the single-dish GBT profile (see Fig. 1). |
| 1.5 GHz VLBA radio continuum peak brightness | 0.19 | not stated | mJy beam−1 | 1 | Its peak brightness reached around 0.19 mJy beam−1. |
| 1.5 GHz VLBA total radio continuum flux density | 2 | not stated | mJy | 1 | Both techniques provided a flux density close to 2 mJy. |
| 1.5 GHz radio continuum brightness temperature | 3e6 | not stated | K | 1 | We have detected compact radio continuum emissions adjacent to the maser positions with a brightness temperature of around 3 × 106 K; Third, we measure the brightness of the 1.4 GHz radio continuum emission of approximately 3 × 106 K. |
| Spatial offset between OH components A/D and continuum emission | 22 | 0.8 | mas | 1 | OH regions B and C lie near the continuum emission, but regions D and A are offset by roughly 22 mas (see Fig. 2).; Based on this equation, we estimate that the error σrel on the relative positions between component A/D and the continuum emission is about 0.8 mas |
| Component A2 OH line amplitude | 28 | 2 | mJy beam−1 | 2 | 2 28 ± 2 40 704 ± 1 28 ± 2 815 ± 77 |
| Component A2 OH line center velocity | 40704 | 1 | km s−1 | 2 | 2 28 ± 2 40 704 ± 1 28 ± 2 815 ± 77 |
| Component A2 OH line FWHM | 28 | 2 | km s−1 | 2 | 2 28 ± 2 40 704 ± 1 28 ± 2 815 ± 77 |
| Component A3 OH line amplitude | 24 | 2 | mJy beam−1 | 2 | 3 24 ± 2 40 745 ± 1 39 ± 3 998 ± 125 |
| Component A3 OH line center velocity | 40745 | 1 | km s−1 | 2 | 3 24 ± 2 40 745 ± 1 39 ± 3 998 ± 125 |
| Component A3 OH line FWHM | 39 | 3 | km s−1 | 2 | 3 24 ± 2 40 745 ± 1 39 ± 3 998 ± 125 |

## Qualitative findings

- The OH emission consists of four compact components (A, B, C, D) and diffuse emission distributed within a rectangular region of ~40 x 30 mas (< 50 mas or < 116 pc).  
  > "The OH emission spatially has four compact components, as well as diffuse emission, and the 3σ signals are distributed in a rectangular region with size of ∼40 × 30 mas." (abstract); "First, we detected OH emission on parsec scales, consisting of four compact components (A, B, C, and D) and diffuse emission distributed in a region smaller than 50 mas (i.e., less than 116 pc)." (5. Summary)
- Both OH-line and radio-continuum emissions spatially coincide with the dense HCN and sub-mm continuum emission.  
  > "Our VLBA observation shows that both OH-line and radio-continuum emissions coincide with dense HCN emission (see Fig. 3)." (4.2. Comparing OH with sub-millimetre line emission)
- The multiple strong OH peaks are blueshifted compared to dense millimetre-wave molecular gas tracers (HCN, HCO+), but align with the blueshifted Na I D absorption and a minor blueshifted wing of the dense gas lines.  
  > "The multiple strong OH peaks are blue-shifted compared to dense millimetre-wave molecular gas tracers, but similar to optical Na I absorption." (abstract); "The HCN and HCO+ lines likely contain a minor blueshifted component, while the OH emission is consistent with this dense gas component (see Figs. 1 and A.1)." (4.2. Comparing OH with sub-millimetre line emission)

## Claim tuples

- H: The nuclear region of IRAS 01298−0744 is still in an active merging process rather than a relaxed post-merger state. | E: Mapped the spatial-velocity structure of OH maser emission with VLBA and compared it with ALMA HCN and HCO+ velocity structures. | R: The OH emission shows a complex velocity structure with multiple peaks and slightly higher velocities at the western and eastern edges, lacking an ordered velocity gradient, similar to HCN and HCO+. | F: The central nuclear region is likely still experiencing a merging phase characterized by intense nuclear activities and has not reached a final relaxed state. | **supported**
- H: The compact OH megamaser emission in IRAS 01298−0744 originates from a nuclear outflow. | E: Compared the VLBA OH line profiles and velocities with systemic velocity, ALMA HCN/HCO+ line profiles, and optical Na I D absorption profiles. | R: Peak OH emission is blueshifted relative to systemic and main HCN/HCO+ velocities, matches the blueshifted Na I D absorption profile, and has broad ~200 km s−1 components consistent with optical shock components. | F: The dominant compact OH maser emission likely stems from a low-velocity nuclear outflow driven by an AGN or starburst. | **supported**
- H: The compact parsec-scale radio continuum emission in IRAS 01298−0744 has a starburst origin. | E: Measured the flux density, size, and brightness temperature of the 1.5 GHz (and archival 8.4 GHz) continuum emission using VLBA observations. | R: Detected compact radio continuum emission adjacent to the masers with total flux ~2 mJy and brightness temperature ~3 × 10^6 K at 1.5 GHz (and ~8.7 × 10^5 K at 8.4 GHz). | F: The brightness temperature is consistent with clustered supernova remnants or luminous radio supernovae, supporting a starburst origin. | **supported**

## Reasoning

- Why this data: High-resolution VLBI observations of bright OH masers are needed to resolve parsec-scale maser and radio continuum structures, while IRAS 01298−0744 is the brightest OHM detected by GBT.  
  > "High-resolution observations are crucial to determining whether OHM galaxies host an AGN or compact starburst and their associations with merging stages and environmental factors (Peng et al. 2020)." (1. Introduction); "IRAS 01298−0744 exhibits a peak flux density of 118 mJy in the 1667 MHz line (see Fig. 1) and is the brightest among all OHMs detected by the Green Bank Telescope (see Willett 2012)." (1. Introduction)
- Why this method: Fitted calibrated visibilities directly with an elliptical Gaussian model to mitigate potential deconvolution effects.  
  > "To measure the total continuum emission, we performed a direct fit of calibrated visibilities using an elliptical" (3. Results)
- Alternative: Broad line profiles at each pixel could either mean the beam size is insufficient to resolve OH clouds at a particular velocity, or that clouds of similar velocities cover a broad area and overlap along the line of sight.  
  > "These broad line profiles at each pixel might mean that the beam size is not enough to resolve the OH clouds at a particular velocity. An alternate scheme is that the clouds of similar velocities cover a broad area." (4.1. The OH line profile and different OH components)
- How they decided it was enough: _not stated_
- Limitation (authors): Observed brightness temperature at 1.5 GHz might be underestimated due to free-free absorption and/or synchrotron self-absorption, representing only a lower limit.  
  > "Consequently, the observed brightness temperature at 1.5 GHz might be underestimated, representing only a lower limit." (4.4. The nature of the continuum emission and association of the OH line)
- Limitation (authors): The 4-sigma compact feature in the archival VLBA X-band image has low S/N and may stem from calibration errors.  
  > "Although VLBA X-band observations have suitable resolution to identify potential compact features, the S/N of the compact feature is low (approximately 4), which may also stem from calibration errors (see the right panel of Fig. A.3)." (4.4. The nature of the continuum emission and association of the OH line)
- Caveat (inferred, ours): Relative astrometric alignment between VLBA L-band and ALMA Band 6 images is limited by phase-referencing calibrator uncertainties and different reference frames, though not explicitly quantified.

## Reproducibility

- Data public (paper): ALMA project 2017.1.00057.S and VLBA project BH237D are stated as archival.  
  > "from the archival Atacama Large Millimeter Array (ALMA) project 2017.1.00057.S (PI M. Imanishi)." (2. Observations and data reduction); "We also tried to find compact radio-continuum emission from the archival VLBA project BH237D (see Table 1)." (4.4. The nature of the continuum emission and association of the OH line)
- Products in archive: Primary-beam-corrected continuum image of ALMA project 2017.1.00057.S is accessible in the ALMA archive.  
  > "For our examination of the sub-millimetre radio-continuum emission, we utilised the primary-beam-corrected image file of Project 2017.1.00057.S, which is readily accessible in the ALMA archive." (2. Observations and data reduction)
- Missing: Exact AIPS calibration parameters and DIFMAP cleaning scripts/windows for VLBA data
- Missing: Exact pixel coordinates for extracted spectra OH1-8
- Missing: CASA version and exact tclean parameters for ALMA line cubes
- Data volume (inferred): A few tens of GB (archival ALMA single-pointing Band 6 data and 8-hour VLBA spectral-line/continuum dataset)
- Score (inferred): 6/5, Archival ALMA data and standard VLBA data with clear observational tables, coordinates, and Gaussian fit results (Tables 1, 2, A.1), though exact software versions and cleaning masks/thresholds are not stated.
- Rediscovery candidate: yes, Both the ALMA (2017.1.00057.S) and VLBA (BW144, BH237D) datasets are in public archives, the extraction regions and coordinates are given, and the main results are quantitative Gaussian line fits and continuum flux/brightness temperature measurements.

## Links

- Method: Martí-Vidal et al. 2014 (Visibility-plane Gaussian model fitting to mitigate deconvolution effects)
- Method: Tarchi et al. 2011 (Equation for relative positional uncertainty between line and continuum emission)
- Companion: Imanishi et al. (2019) (Original publication and imaging setup for the archival ALMA HCN and HCO+ observations of IRAS 01298−0744)
- Related: SDSS
- Related: VLASS
- Related: NVSS

## Checks

```json
{
 "quotes": 94,
 "quotes_ok": 94,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 1,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 46,
  "rate": 0.639
 },
 "evidence_ok": true
}
```
