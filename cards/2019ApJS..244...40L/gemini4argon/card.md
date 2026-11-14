# Automated Mining of the ALMA Archive in the COSMOS Field (A<SUP>3</SUP>COSMOS). I. Robust ALMA Continuum Photometry Catalogs and Stellar Mass and Star Formation Properties for ∼700 Galaxies at z = 0.5-6

`2019ApJS..244...40L` | The Astrophysical Journal Supplement Series 2019 | first author: Liu, Daizhong | arXiv: 1910.12872 | DOI: 10.3847/1538-4365/ab42da

Card schema 1.0 | model gemini-4-argon | depth full | type data_release_or_catalog

## Science

- Fields: high_z_galaxies, star_formation
- Question: How to systematically mine inhomogeneous public ALMA archival data in the COSMOS field to produce robust continuum photometry catalogs and derive stellar mass and star formation properties for high-redshift galaxies.  
  > "To increase the usability of these data for studies deepening our understanding of galaxy evolution, we have developed automated mining pipelines for the ALMA archive in the COSMOS field (A3COSMOS)" (abstract); "This work provides the foundation for a systematic exploitation of the (sub-)mm continuum as a proxy for cold dust and gas for a diverse and large sample of high-redshift galaxies." (1. INTRODUCTION)
- Target **COSMOS field**: coordinates R.A. = 10:00:28.6, decl. = +02:12:21.0 (J2000)  
  > "We limit our selection to within the COSMOS field (R.A. = 10:00:28.6, decl. = +02:12:21.0, J2000; Scoville et al. 2007)" (2. DATA AND PHOTOMETRY); "The final galaxy catalog (version `20180201` ) contains 676 galaxies in the range of _z_ = 0 _._ 25 _−_ 5 _._ 67" (6. SUMMARY); z/distance z = 0.25-5.67  
  > "We limit our selection to within the COSMOS field (R.A. = 10:00:28.6, decl. = +02:12:21.0, J2000; Scoville et al. 2007)" (2. DATA AND PHOTOMETRY); "The final galaxy catalog (version `20180201` ) contains 676 galaxies in the range of _z_ = 0 _._ 25 _−_ 5 _._ 67" (6. SUMMARY); distance from Multi-wavelength spectroscopic and photometric redshift compilations in the COSMOS field  
  > "We limit our selection to within the COSMOS field (R.A. = 10:00:28.6, decl. = +02:12:21.0, J2000; Scoville et al. 2007)" (2. DATA AND PHOTOMETRY); "The final galaxy catalog (version `20180201` ) contains 676 galaxies in the range of _z_ = 0 _._ 25 _−_ 5 _._ 67" (6. SUMMARY)

## Data provenance

- ALMA projects: 2011.0.00064.S, 2011.0.00539.S, 2011.0.00742.S, 2012.1.00323.S, 2012.1.00523.S, 2012.1.00536.S, 2012.1.00919.S, 2012.1.00978.S, 2013.1.00034.S, 2013.1.00118.S, 2013.1.00151.S, 2013.1.00171.S, 2013.1.00208.S, 2013.1.00668.S, 2013.1.00815.S, 2013.1.00914.S, 2013.1.01258.S, 2013.1.01292.S, 2015.1.00026.S, 2015.1.00122.S, 2015.1.00137.S, 2015.1.00299.S, 2015.1.00379.S, 2015.1.00388.S, 2015.1.00540.S, 2015.1.00664.S, 2015.1.00704.S, 2015.1.00861.S, 2015.1.00862.S, 2015.1.00928.S, 2015.1.01074.S, 2015.1.01111.S, 2015.1.01171.S, 2015.1.01495.S, 2015.1.01590.S, 2015.A.00026.S, 2016.1.00478.S, 2016.1.00735.S, 2016.1.01208.S
- bands: Band 3, Band 4, Band 5, Band 6, Band 7, Band 8, Band 9  
  > "Info Type Band 3 Band 4 Band 5 Band 6 Band 7 Band 8 Band 9" (Table 1)
- frequencies and spectral setup: 44% at ~870 um, 49% at ~1.0-1.5 mm, ~1% at ~1.9-2.3 mm, ~6% at ~2.5-3.4 mm; spectral windows aggregated into continuum  
  > "the spectral windows (SpWs) of each target are aggregated into a single continuum image calculated at the central frequencies of these SpWs" (2.1. ALMA Continuum Images); "about 44% of the data are at _∼_ 870 _µ_ m, about 49% at _∼_ 1 _._ 0 _−_ 1 _._ 5 mm (mostly 1 _._ 25 mm), _∼_ 1% at _∼_ 1 _._ 9 _−_ 2 _._ 3 mm and _∼_ 6% at _∼_ 2 _._ 5 _−_ 3 _._ 4 mm." (3.1.5. Final Corrections)
- continuum bandwidth: ~8 GHz  
  > "In special cases, these lines will dominate the emission from the whole bandwidth, e.g., mostly _∼_ 8 GHz of the current ALMA receiver." (4.5. Correcting significant contribution from emission lines)
- arrays: 12m array  
  > "Given the large number of antennas in the 12m array, the instantaneous dirty beam for a short integration ( _∼_ 30 seconds) as used for many programs has very low sidelobes" (2.1. ALMA Continuum Images)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: >= 0.1 arcsec (mean beam size 0.305 to 2.164 arcsec across Bands 3-9; <0.1 arcsec excluded)  
  > "Therefore, these ≲ 1% very high resolution ( _θ_ Maj _,_ beam _<_ 0 _._ 1 _[′′]_ ) images are excluded from our analysis." (2.1. ALMA Continuum Images); "Mean Beam Size [arcsec] 2.164 1.098 1.548 1.202 0.772 0.526 0.305" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: Mean RMS noise 0.025 to 1.757 mJy/beam across Bands 3-9 (0.077 in Band 6, 0.160 in Band 7)  
  > "Mean RMS Noise [mJy/beam] 0.039 0.025 0.090 0.077 0.160 0.034 1.757" (Table 1)
- time on source: ~30 seconds for many programs  
  > "the instantaneous dirty beam for a short integration ( _∼_ 30 seconds) as used for many programs has very low sidelobes" (2.1. ALMA Continuum Images)
- observing dates: public before Jan. 2nd, 2018  
  > "We show the pointings of all public ALMA data for the COSMOS field as of Jan. 2nd, 2018 in Fig. 2" (2. DATA AND PHOTOMETRY)
- pi or archival as stated: archival  
  > "we have developed automated mining pipelines for the ALMA archive in the COSMOS field (A3COSMOS)" (abstract)
- Other facility **HST/ACS**: i-band image cutouts for counterpart association  
  > "_Hubble_ _Space_ _Telescope_ ( _HST_ ) ACS _i_ -band image from Capak et al. (2007);" (4.2. Examining counterpart association)
- Other facility **VISTA / UltraVISTA**: Ks-band image cutouts for counterpart association  
  > "UltraVISTA _K_ _s_ -band image from McCracken et al. (2010, 2012);" (4.2. Examining counterpart association)
- Other facility **Spitzer/IRAC (SPLASH)**: 3.6 um image cutouts for counterpart association  
  > "_Spitzer_ IRAC 3.6 _µ_ m image from the SPLASH survey (PI: P. Capak);" (4.2. Examining counterpart association)
- Other facility **VLA**: 3 GHz image cutouts for counterpart association  
  > "and VLA 3 GHz image from Smolčić et al. (2017)." (4.2. Examining counterpart association)
- Other facility **Herschel/PACS**: 100 um background image for pointing map  
  > "The background image is the _Herschel_ PACS 100 _µ_ m data from the PACS Evolutionary Probe survey (PEP; Lutz et al. 2011)." (Figure 2 caption)
- External data: COSMOS2015 optical/near-IR prior catalog, 3 arcsec aperture photometry, and photometric redshifts  
  > "COSMOS2015 catalog 1 _._ 8 1182108 1182108 738420 VISTA _z Y JHK_ _s_ 24.0 (3 _σ_, 3 _[′′]_, _K_ _s_ ) _∼_ 1 _[′′]_ (Laigle et al. 2016)" (Table 2); "(2016) catalog, and use the 3 _[′′]_ diameter aperture fluxes to be consistent with Laigle et al. (2016)" (4.3 Combining multi-wavelength photometry and prior) [from Laigle et al. (2016)]
- External data: Ks-band prior catalog  
  > "_K_ _s_ -band catalog 1 _._ 6 _[f]_ 263229 18536 10799 VISTA _K_ _s_ 24.35 (3 _σ_, 2 _[′′]_ _._ 1) _∼_ 1 _[′′]_ (Muzzin et al. 2013) _[f]_" (Table 2) [from Muzzin et al. (2013)]
- External data: i-band prior catalog and HST ACS i-band image  
  > "_i_ -band catalog 1 _._ 8 386125 31159 30146 CFHT _i_ _[⋆]_ + 26.2 (5 _σ_, 3 _[′′]_ ) _∼_ 0 _[′′]_ _._ 5 (Capak et al. 2007) _Subaru_ _i_ [+]" (Table 2) [from Capak et al. (2007)]
- External data: SPLASH IRAC supplementary prior catalog  
  > "SPLASH IRAC 1 _._ 6 5390 4685 3690 _Spitzer_ /IRAC 25.5 (3 _σ_ ) _∼_ 1 _[′′]_ _._ 6 supplementary catalog _[g]_ 3.6 + 4.5 _µ_ m" (Table 2) [from SPLASH (PI: P. Capak; I. Davidzon; priv. comm.)]
- External data: VLA 3 GHz prior catalog and image  
  > "VLA catalog 2 10922 1042 644 VLA 3 GHz 2 _._ 3 _µ_ Jy (1 _σ_ ) _∼_ 0 _[′′]_ _._ 75 (Smolčić et al. 2017)" (Table 2) [from Smolčić et al. (2017)]
- External data: Spitzer/IRAC prior catalog  
  > "IRAC catalog 2 _._ 3 347332 55346 54642 _Spitzer_ /IRAC 24.01 (5 _σ_, _∼_ 1 _[′′]_ _._ 6 (Sanders et al. 2007) 3 _._ 6 _−_ 8 _._ 0 _µ_ m 3.6 _µ_ m)" (Table 2) [from Sanders et al. (2007)]
- External data: Super-deblended far-IR/(sub-)mm/radio photometry and photo-z catalog  
  > "Further, we adopt the far-IR/(sub-)mm/radio photometry from Jin et al. (2018)." (4.3. Combining multi-wavelength photometry and prior redshifts in the literature) [from Jin et al. (2018)]
- External data: Spectroscopic redshift compilation in COSMOS  
  > "Spectroscopic redshifts also exist for _∼_ 7 _._ 1 _×_ 10 [4] galaxies, from the latest compilation by M. Salvato et al. (version Sept. 1st, 2017; available internally in the COSMOS collaboration)" (2. DATA AND PHOTOMETRY) [from M. Salvato et al. (version Sept. 1st, 2017)]
- External data: Photometric redshifts and stellar mass functions for z > 2.5 galaxies  
  > "the Davidzon et al. (2017) photometric catalog for the same UltraVISTA galaxies as Laigle et al. (2016) but with optimized SED fitting for _z_ _>_ 2 _._ 5 sources;" (4.3. Combining multi-wavelength photometry and prior redshifts in the literature) [from Davidzon et al. (2017)]
- External data: Photometric redshifts, AGN classifications, and SED3FIT stellar masses for radio-detected galaxies  
  > "the Delvecchio et al. (2017) photometric catalog for radio-detected galaxies;" (4.3. Combining multi-wavelength photometry and prior redshifts in the literature); "In Fig. 24 we further compare our final _M_ _∗_ to the Delvecchio et al. (2017) SED3FIT fitted _M_ _∗_ for 396 sources in common" (4.6. Obtaining galaxy properties from SED fitting) [from Delvecchio et al. (2017)]
- External data: Photometric redshifts for X-ray-detected AGNs  
  > "and the Salvato et al. (2011) photometric catalog for X-ray-detected active galactic nuclei (AGNs)." (4.3. Combining multi-wavelength photometry and prior redshifts in the literature) [from Salvato et al. (2011)]
- Simulation/model as data: Full-parameter-space (FULL) Monte Carlo simulation uniformly sampling S/N_peak from 2.5 to 100 and source-to-beam size ratio from 0.1 to 6  
  > "We start with a full-parameter-space simulation (hereafter “FULL” simulation) in which the full parameter space of flux density and size is uniformly sampled: S _/_ N peak ranges from 2.5 to 100 in logarithmic intervals, and source major-axis size to beam major-axis size ratio ranges from 0.1 to 6." (3. MONTE CARLO SIMULATIONS)
- Simulation/model as data: Physically-motivated (PHYS) Monte Carlo simulation mimicking observed galaxy stellar mass functions, star-forming main sequence, 2SFM starburst/MS classification, and size evolution  
  > "We create another physically-motivated MC simulation, hereafter “PHYS” simulation, where we simulate sources mimicking observed galaxy stellar mass functions (SMFs; e.g., Davidzon et al. 2017), star-forming MS relation (MS; e.g., Sargent et al. 2014)" (3. MONTE CARLO SIMULATIONS)
- Simulation/model as data: Simulated 2 deg^2 galaxy catalog with strong- and weak-lensing magnification from Bethermin et al. (2017)  
  > "Lastly, our low number of strongly lensed sources is consistent with the analytic galaxy modeling of Béthermin et al. (2017; see also Béthermin et al. 2012b)." (4.9. The effect of galaxy-galaxy gravitational lensing)

## Processing

### Calibration

- pipeline or manual: scriptForPI.py  
  > "These datasets are calibrated with the Common Astronomy Software Applications (CASA; McMullin et al. 2007) using the `scriptForPI.py` scripts provided by the Joint ALMA Observatory together with the archived raw data." (2.1. ALMA Continuum Images)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: no, raw data recalibrated using scriptForPI.py and re-imaged  
  > "These datasets are calibrated with the Common Astronomy Software Applications (CASA; McMullin et al. 2007) using the `scriptForPI.py` scripts provided by the Joint ALMA Observatory together with the archived raw data." (2.1. ALMA Continuum Images); "Calibrated visibilities are imaged and “cleaned” — i.e., deconvolved with the “dirty” beam — with the CASA imaging pipeline version `4.7.2` ." (2.1. ALMA Continuum Images)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA imaging pipeline version 4.7.2 in continuum + automatic mode (manual CASA task clean for a few Cycle 0 projects)  
  > "Calibrated visibilities are imaged and “cleaned” — i.e., deconvolved with the “dirty” beam — with the CASA imaging pipeline version `4.7.2` ." (2.1. ALMA Continuum Images); "These projects are thus imaged with the CASA task `clean` with input parameters manually set using a similar imaging and “cleaning” strategy to the CASA imaging pipeline" (2.1. ALMA Continuum Images)
- deconvolver: multi-frequency synthesis (MFS) with nterms=2  
  > "the spectral windows (SpWs) of each target are aggregated into a single continuum image calculated at the central frequencies of these SpWs using the multi-frequency synthesis ( `MFS` ) algorithm with `nterms=2` ." (2.1. ALMA Continuum Images)
- weighting robust: Briggs with robust=2 (robust=0.5 in <10% of images with obvious artifacts)  
  > "The pipeline is operated in “continuum” + “automatic” mode, leaving all but the weight parameters (set to “Briggs” with `robust=2` ) to their default values." (2.1. ALMA Continuum Images); "In case of obvious image artifacts in the cleaned images (as found by visual inspection, _<_ 10%), we rerun the CASA imaging pipeline flagging corrupted baselines and/or adopting `robust=0.5` ." (2.1. ALMA Continuum Images)
- uv taper: _not stated_
- cell size: 5 pixels per synthesized beam  
  > "The output images sample the synthesized beam with 5 pixels and are masked where the PBA is _<_ 0 _._ 2." (2.1. ALMA Continuum Images)
- image size: _not stated_
- masking: automatic pipeline masking based on dirty image noise and dynamic range, stopping criterion S/N = 4; primary beam attenuation masked where PBA < 0.2  
  > "The parameters controlling the deconvolution process (i.e., masked pixels, maximum number of iterations and stopping threshold) are automatically and homogeneously set by the pipeline based on the noise properties and dynamic range of the “dirty” images" (2.1. ALMA Continuum Images); "The imaging pipeline uses masks to identify regions of bright emission prior to cleaning and the stopping criterion is set to a signal-to-noise ratio (S/N) = 4." (2.1. ALMA Continuum Images)
- multiscale scales: _not stated_
- continuum subtraction: none during imaging (all SpWs aggregated; strong line contribution corrected post-facto in catalog)  
  > "Note that although the aggregation of all SpWs available for a given target optimizes the sensitivities of our continuum images, it does not consider any possible line contamination." (2.1. ALMA Continuum Images)
- line free channels: _not stated_
- primary beam correction: both PBA-corrected and uncorrected images released; photometry performed on uncorrected images and PBA correction applied to cataloged fluxes at source central position (masked for PBA < 0.2)  
  > "The data products released here include all “clean” continuum images corrected and uncorrected for pri" (2.1 ALMA Continuum Images); "We use the primary-beam-attenuation-uncorrected images because they have the advantage of a constant noise across the field of view, and thus source extraction can be run with uniform parameters across them." (2.2. Blind Source Extraction)
- array combination: data from different projects for the same source are not combined  
  > "Currently, data for the same source taken at the same frequency arising from different projects are not combined." (2.1. ALMA Continuum Images)
- smoothing: _not stated_
- final beam: mean beam size per band: 2.164'' (Band 3), 1.098'' (Band 4), 1.548'' (Band 5), 1.202'' (Band 6), 0.772'' (Band 7), 0.526'' (Band 8), 0.305'' (Band 9)  
  > "Mean Beam Size [arcsec] 2.164 1.098 1.548 1.202 0.772 0.526 0.305" (Table 1)
- final rms: mean RMS noise per band: 0.039 (Band 3), 0.025 (Band 4), 0.090 (Band 5), 0.077 (Band 6), 0.160 (Band 7), 0.034 (Band 8), 1.757 (Band 9) mJy/beam  
  > "Mean RMS Noise [mJy/beam] 0.039 0.025 0.090 0.077 0.160 0.034 1.757" (Table 1)

### Inherited from earlier work

- Aperture photometry (getpix) method measuring peak and integrated flux densities in concentric apertures from 0.25'' to 2'' in steps of 0.25'' and pre-selection thresholds (S/N_total > 2 or S/N_peak > 3.6)  
  > "Following Scoville et al. (2014, 2016, 2017), we measure both flux densities in a series of apertures with radii from 0 _[′′]_ _._ 25 to 2 _[′′]_ in steps of 0 _[′′]_ _._ 25." (2.4. Prior Source Fitting); "S _/_ N peak _>_ 3 _._ 6 sources (same as Scoville et al. 2017) as valid detections." (2.4 Prior Source Fitting) [from Scoville et al. (2014, 2016, 2017)]
- Gaussian fitting parameter error formulae  
  > "Finally, the errors of each fitted parameter (peak flux, total flux, and each size parameter) are computed using the formulae of Gaussian fitting errors calibrated by Condon (1997)." (2.2. Blind Source Extraction) [from Condon (1997)]
- 2D parameterization of flux bias and error as functions of S/N_peak and Theta_beam  
  > "we bin all simulated and recovered sources in the 2D parameter space of S _/_ N peak and Θ beam, and consider flux bias and error to be functions of these two parameters (Condon 1997; Bondi et al. 2003, 2008; Schinnerer et al. 2010; Jiménez-Andrade et al. 2019)." (3.1. Analyses of the “FULL” and “PHYS” Simulations) [from Condon (1997); Bondi et al. (2003, 2008); Schinnerer et al. (2010); Jiménez-Andrade et al. (2019)]
- 2-star-formation-mode (2SFM) recipe for simulating main-sequence and starburst galaxies  
  > "In detail, we follow the two-star-formation-mode (2SFM) recipe (Sargent et al. 2012, 2014; Béthermin et al. 2012a)" (C.2.1. Source simulation) [from Sargent et al. (2012, 2014); Béthermin et al. (2012a)]
- IR-to-radio SED modeling for simulated galaxies in PHYS simulation  
  > "Then we generate an IR-to-radio SED for each model galaxy according to the redshift, stellar mass and SFR, following the SED modeling in Liu et al. (2018), which is based on Magdis et al. (2012)" (C.2.1. Source simulation) [from Liu et al. (2018); Magdis et al. (2012)]
- uv-plane spectral line search methodology  
  > "The line search is done in the _uv_ -plane adapting the methodology of Silverman et al. (2015b) and D. Liu et al. (2019, in preparation), with CASA and GILDAS." (4.5. Correcting significant contribution from emission lines) [from Silverman et al. (2015b); D. Liu et al. (2019, in preparation)]

### Not stated but needed to reproduce (our reading)

- Exact CASA versions used to run scriptForPI.py for calibrating each archival dataset
- List of the <10% of images where corrupted baselines were flagged or robust=0.5 was adopted instead of robust=2
- Exact tabulated values or polynomial coefficients for the PHYS simulation 2D flux bias (eta_bias) and flux error (eta_error) lookup grids
- Access to the internal COSMOS spectroscopic redshift compilation by M. Salvato et al. (version Sept. 1st, 2017)
- Hyperparameters and trained weights of the scikit-learn Gaussian Process classifier used for counterpart association

## Analysis recipe

1. **Query archive, calibrate visibilities, and create continuum images**: Query ALMA archive within 2 deg of COSMOS center, calibrate raw visibilities with scriptForPI.py, and image/clean all spectral windows into continuum maps using MFS (nterms=2) and Briggs weighting (robust=2), excluding beam < 0.1 arcsec.  
  > "We start by querying the ALMA archive with the `Python` package `astroquery` Ginsburg et al. 2019, retrieving all projects publicly available within a search radius of 2 degrees centered on the COSMOS field." (2.1. ALMA Continuum Images); "Calibrated visibilities are imaged and “cleaned” — i.e., deconvolved with the “dirty” beam — with the CASA imaging pipeline version `4.7.2` ." (2.1. ALMA Continuum Images)
   - software: astroquery, CASA, CASA imaging pipeline, clean
   - parameter: search radius = 2 degrees, weighting = Briggs with robust=2 (or 0.5 for artifacts), MFS nterms=2, stopping criterion S/N = 4, 5 pixels per beam, PBA >= 0.2, beam >= 0.1 arcsec  
  > "The pipeline is operated in “continuum” + “automatic” mode, leaving all but the weight parameters (set to “Briggs” with `robust=2` ) to their default values." (2.1. ALMA Continuum Images); "The output images sample the synthesized beam with 5 pixels and are masked where the PBA is _<_ 0 _._ 2." (2.1. ALMA Continuum Images)
   - fitting: _not stated_
   - validation: Visual inspection for artifacts (<10% re-imaged) and comparison of 1-sigma rms noise against ALMA archive QA2 continuum images.  
  > "As a test, we measure the 1 _σ_ sensitivities (rms noise) of our images ( _σ_ A 3 ) and compare with those measured in the continuum images available in the ALMA archive" (2.1. ALMA Continuum Images)
2. **Blind source extraction on PBA-uncorrected continuum images**: Identify emission islands and fit multiple 2D Gaussians on PBA-uncorrected images using PyBDSF, grouping Gaussians of the same island into one source.  
  > "Next, PyBDSF fits multiple two-dimensional Gaussians to each “island” depending on the number of peaks identified within it. Thirdly, all Gaussians of the same “island” are grouped into one source" (2.2 Blind Source Extraction); "all Gaussians of the same “island” are grouped into one source, with the summed flux being the integrated source flux" (2.2. Blind Source Extraction)
   - software: PyBDSF, AIPS DECONV.FOR
   - parameter: thresh_pix = 4, thresh_isl = 3  
  > "First, the code identifies “islands” of emission, i.e., with the peak pixel emission above 4 times the rms noise ( `thresh_pix` = 4), and surrounded by contiguous pixels with values all greater than 3 times the rms noise ( `thresh_isl` = 3)." (2.2. Blind Source Extraction)
   - assumption: Constant noise across the PBA-uncorrected field of view; single PBA factor at source central position  
  > "We use the primary-beam-attenuation-uncorrected images because they have the advantage of a constant noise across the field of view" (2.2. Blind Source Extraction); "Given that each source represents a high-redshift galaxy with a typical size of 0.5–2 _[′′]_, much smaller than the primary beam" (2.2 Blind Source Extraction)
   - fitting: 2D Gaussian fitting with parameter errors initially from Condon (1997) formulae  
  > "Next, PyBDSF fits multiple two-dimensional Gaussians to each “island” depending on the number of peaks identified within it." (2.2. Blind Source Extraction)
   - validation: Thresholds tested via mock source injection and recovery; inverted-image fitting for spurious fraction.  
  > "These thresholds are obtained from a series of tests by introducing mock sources into the ALMA images and recovering them with PyBDSF." (2.2. Blind Source Extraction)
3. **Compile prior source master catalog and perform prior source fitting**: Cross-match 6 multi-wavelength COSMOS catalogs with 1 arcsec radius, correct mean astrometric offsets, pre-select candidates via aperture photometry (getpix), and iteratively fit point-source, circular Gaussian, and Sersic profiles using GALFIT.  
  > "we find out each uniquely-matched group among the prior catalogs (with matching radius 1 _[′′]_ ) and add into the master catalog only the source coming from the highest-quality" (2.3. Prior Source Master Catalog); "This first getpix step also provides guidance for the prior source fitting using galfit (Peng et al. 2002, 2010) in the next step." (2.4. Prior Source Fitting)
   - software: getpix, GALFIT
   - parameter: master catalog matching radius = 1 arcsec; getpix apertures = 0.25'' to 2'' in 0.25'' steps; pre-selection S/N_total > 2 or S/N_peak > 3.6; position variation limit = 0.7 arcsec; size upper boundary = 3.0 arcsec  
  > "S _/_ N peak _>_ 3 _._ 6 sources (same as Scoville et al. 2017) as valid detections." (2.4 Prior Source Fitting); "and allow their positions to vary by at most 0 _[′′]_ _._ 7" (2.4 Prior Source Fitting)
   - assumption: Image background is zero  
  > "For each fit, we ensure that the image background is zero (as already verified by the close-to-zero means of the distributions of the pixel values from the ALMA images)." (2.4. Prior Source Fitting)
   - fitting: Iterative GALFIT chi-square minimization (pass 1: fixed-position point source; pass 2: position varied up to 0.7''; pass 3: circular Gaussian / Sersic profile)  
  > "To optimize the galfit fitting for source fluxes as well as sizes, an iterative approach is adopted: After the first-pass fitting with point-source models to all galfit priors fixed at their original positions," (2.4 Prior Source Fitting)
   - validation: Compared against PyBDSF blind extraction, GILDAS uv_fit on 301 pointings, getpix aperture photometry, and inverted-image fitting.  
  > "task to fit Gaussian and/or point-source models then compare the total flux with those measured from the image-plane galfit and PyBDSF fitting." (2.6 Comparison to uv-plane Source Fitting Results); "We run our photometry tools (based on PyBDSF and galfit) on the inverted images (i.e., the sign of each pixel value is inverted) to estimate the fraction (and probability) of spurious detections" (2.8. Inverted-image Fitting and the Fraction of Spurious Detection)
4. **Monte Carlo simulations for flux bias correction, error re-estimation, and completeness**: Run FULL and PHYS Monte Carlo simulations by injecting Gaussian mock sources into PyBDSF residual images of 150+ representative pointings, recovering them with PyBDSF and GALFIT, and deriving 2D lookup corrections as functions of S/N_peak and Theta_beam.  
  > "In our simulations, we create artificial sources (of Gaussian shape), insert them into residual images (after blind extraction photometry), and recover them with our photometry pipelines." (3. MONTE CARLO SIMULATIONS); "We choose the “PHYS” simulation for the final correction, considering the discussion in the previous sections, i.e., “PHYS” simulation is more representative of our real data." (3.1.5. Final Corrections)
   - software: PyBDSF, GALFIT
   - parameter: 150+ representative images; 4225 realizations per image for FULL, 273 for PHYS; cross-match radius = 1.5 arcsec for PyBDSF completeness  
  > "For each selected image, we perform the “FULL” and “PHYS” type simulations 4225 and 273 times respectively" (3. MONTE CARLO SIMULATIONS); "We cross-match the PyBDSF source recovery catalog to the simulated catalog for each image by coordinate using a search radius of 1.5 _[′′]_" (3.2. Completeness)
   - assumption: Gaussian source morphology with axis ratio 0.2 to 1.0; PHYS simulation assumes 2SFM, Davidzon et al. (2017) SMF, Sargent et al. (2014) MS, van der Wel et al. (2014) and Fujimoto et al. (2017) sizes  
  > "where we simulate sources mimicking observed galaxy stellar mass functions (SMFs; e.g., Davidzon et al. 2017), star-forming MS relation (MS; e.g., Sargent et al. 2014) and starburst/MS classification" (3. MONTE CARLO SIMULATIONS); "The simulated source is assumed to be of Gaussian shape (the minor-axis FWHM is generated with an axis ratio randomly picked between 0.2 to 1.0)." (C.1.1. Source simulation and injection)
   - fitting: Function fitting of the form a * S/N_peak^m + b * S/N_peak^n and interpolation in (S/N_peak, Theta_beam) bins  
  > "Solid red lines are function fitting (with the form _a_ S _/_ N peak _[m]_ [+] _[ b]_ [ S] _[/]_ [N] peak _[n]_ [)] [to] [the] [flux] [bias] [data] [points]" (Figure 11 caption)
   - validation: Verified that normalized flux difference histograms (S_sim - S_rec^corr)/sigma_S_rec^corr follow a mean=0, sigma=1 Gaussian distribution.  
  > "The final histograms nicely agree with the mean = 0, sigma = 1 1D Gaussian." (C.3. Final statistical behaviour of corrected fluxes and errors)
5. **Catalog merging and machine-learning counterpart association**: Select blind detections with S/N_peak > 5.40 and prior detections with S/N_peak > 4.35, cross-match within 1.0 arcsec, and classify counterpart reliability using a Gaussian Process classifier trained on visual inspection and multi-wavelength cutout parameters.  
  > "We apply an S _/_ N peak cut at 5.40 to our blind source extraction catalog (Sect. 2.2) and an S _/_ N peak cut at 4.35 to our prior source fitting catalog (Sect. 2.4)." (4.1. Combining the two photometric catalogs); "After testing a number of different classifiers available in scikit-learn, we decide to use the Gaussian Process (GP) classifier, which implements Gaussian Processes for probabilistic classification." (4.2. Examining counterpart association)
   - software: scikit-learn
   - parameter: S/N_peak > 5.40 (blind), S/N_peak > 4.35 (prior); cross-match radius = 1.0 arcsec; training/validation split = 60%/40%; features = Sep., S/N_ALMA, S/N_Ref., S./Ref., Ext., crowdedness, clean  
  > "To merge the two photometric catalogs, we spatially cross-match their sources with a radius of 1.0 _[′′]_" (4.1. Combining the two photometric catalogs); "Then, we randomly select 60% of the sample with visual classifications for training, leaving the final 40% for model validation." (4.2. Examining counterpart association)
   - fitting: Supervised Gaussian Process probabilistic classification  
  > "we decide to use the Gaussian Process (GP) classifier, which implements Gaussian Processes for probabilistic classification." (4.2. Examining counterpart association)
   - validation: 40% validation sample achieved ~96.5% accuracy (97% overall agreement with median of three visual inspectors).  
  > "Running our trained model on the validation sample gave an accuracy of _∼_ 96 _._ 5%." (4.2. Examining counterpart association)
6. **Predict and subtract strong (sub-)mm emission line contamination**: Predict CO, [C I], [C II], and [N II] line luminosities from empirical line-L_IR relations using source redshift and SFR, check whether lines fall into the ALMA spectral windows, and subtract predicted line flux contribution from continuum.  
  > "Meanwhile, we obtain the exact frequency setups for each ALMA observation from the ALMA archive, and identify the predicted strong (sub-)mm lines within the frequency setups." (4.5. Correcting significant contribution from emission lines); "We estimate the line contribution to the measured continuum by dividing the predicted line flux by the total bandwidth and compare that to the measured continuum." (4.5. Correcting significant contribution from emission lines)
   - software: CASA, GILDAS
   - parameter: lines predicted: CO (2 <= J_upper <= 10), [C I] (370, 609 um), [N II] (122, 205 um), [C II] (158 um)  
  > "Our pipeline uses the redshift and SFR (and IR color, e.g., rest-frame _S_ 70 _µ_ m _/S_ 160 _µ_ m from SEDs, when necessary) to predict for each source the low- to high- _J_ CO (upper level quantum number 2 _≤_ _J_ upper _≤_ 10)" (4.5. Correcting significant contribution from emission lines)
   - assumption: Empirical line-L_IR correlations from De Looze et al. (2011), Zhao et al. (2013, 2016), Sargent et al. (2014), Liu et al. (2015), Valentino et al. (2018)  
  > "The line prediction follows empirical luminosity–luminosity correlations: [C ii]– _L_ IR correlation from De Looze et al. (2011)" (4.5. Correcting significant contribution from emission lines)
   - fitting: _not stated_
   - validation: Extracted lines in data cubes for ~50 sources with >20% predicted contamination and compared against 234 literature line detections.  
  > "Our prediction suggests that _∼_ 50 ( _∼_ 7%) sources have (sub-)mm lines contributing more than 20% to the measured continuum. We looked into their data cubes and found that most of them do have line emission as predicted" (4.5. Correcting significant contribution from emission lines)
7. **Multi-wavelength SED fitting to derive stellar masses, IR luminosities, and SFRs**: Fit UV-to-mm/radio SEDs with MAGPHYS at fixed prior redshifts (iterating over inconsistent prior-z values and with/without 24 um data) and with MAGPHYS+photo-z to obtain uncertainties, flagging >5 sigma ALMA SED-excess outliers.  
  > "We use MAGPHYS (da Cunha et al. 2008, 2015) [22] for the SED fitting, as it has rich stellar SED libraries" (4.4 SED fitting); "for log _M_ _∗_ and log SFR in our final galaxy catalog, we take the uncertainties from the photo- _z_ SED fitting which includes the redshift uncertainty, while keep the best-fit values still from the best prior- _z_ fit." (4.4. SED fitting)
   - software: MAGPHYS, MAGPHYS+photo-z, Crab.Toolkit.michi2
   - parameter: inconsistent prior-z threshold Delta z > 0.15 * (1+z); SED-excess outlier threshold S_OBS / S_SED > 1.77 (5 sigma); photo-z range z = 0 to 8  
  > "for galaxies with inconsistent prior- _z_ (∆ _z_ _>_ 0 _._ 15 _×_ (1+ _z_ )) from the above catalogs, we run SED fitting for each inconsistent prior- _z_ and take the one with minimum- _χ_ [2] at the ALMA bands as our best fit." (4.3. Combining multi-wavelength photometry and prior redshifts in the literature); "Its upper 5- _σ_ envelope corresponds to _S_ OBS _/S_ SED = 1 _._ 77, above which we do find 3% outliers." (4.4. SED fitting)
   - assumption: Flat LambdaCDM cosmology (H_0 = 70 km s^-1 Mpc^-1, Omega_M = 0.3, Omega_0 = 0.7), Chabrier (2003) IMF, energy balance between UV/optical dust attenuation and IR/mm dust emission, Kennicutt (1998) SFR_IR calibration  
  > "Throughout the paper, we adopt a flat ΛCDM cosmology with _H_ 0 = 70 km s _[−]_ [1] Mpc _[−]_ [1], Ω M = 0 _._ 3, Ω 0 = 0 _._ 7, and a Chabrier (2003) initial mass function (IMF)." (1. INTRODUCTION); "It assumes an energy balance between the energy attenuated by dust in the UV/optical and that radiated by dust at IR/mm wavelengths." (4.4. SED fitting); "Our final SFRs are computed from the IR luminosity with the Kennicutt (1998) calibration and assuming a Chabrier (2003) IMF:" (4.6. Obtaining galaxy properties from SED fitting)
   - fitting: Chi-square template library fitting with PDF marginalization (68th percentiles)  
  > "For each property, MAGPHYS gives a minimum- _χ_ [2] (i.e., best-fit) value, as well as the median and the lower and upper 68 [th] percentiles of the PDF." (4.6. Obtaining galaxy properties from SED fitting)
   - validation: Compared derived M_* against Delvecchio et al. (2017) SED3FIT (with AGN templates) for 396 sources, tested two-component stellar+AGN fits with michi2, and compared MAGPHYS+photo-z against spec-z.  
  > "In Fig. 24 we further compare our final _M_ _∗_ to the Delvecchio et al. (2017) SED3FIT fitted _M_ _∗_ for 396 sources in common (with consistent redshifts and coordinates)." (4.6. Obtaining galaxy properties from SED fitting)

## Software

- **astroquery** : Querying the ALMA archive for publicly available projects in the COSMOS field  
  > "We start by querying the ALMA archive with the `Python` package `astroquery` Ginsburg et al. 2019" (2.1. ALMA Continuum Images)
- **CASA** 4.7.2: Calibrating raw ALMA visibilities with scriptForPI.py, continuum imaging via the imaging pipeline and clean task, uvmodelfit testing, and uv-plane line searches  
  > "These datasets are calibrated with the Common Astronomy Software Applications (CASA; McMullin et al. 2007) using the `scriptForPI.py` scripts" (2.1. ALMA Continuum Images); "Calibrated visibilities are imaged and “cleaned” — i.e., deconvolved with the “dirty” beam — with the CASA imaging pipeline version `4.7.2` ." (2.1. ALMA Continuum Images)
- **PyBDSF** : Blind source extraction and 2D Gaussian fitting on ALMA continuum images  
  > "We use the Python Blob Detector and Source Finder (aka PyBDSM or PyBDSF; hereafter PyBDSF; Mohan & Rafferty 2015) [5] to find sources blindly and extract their flux and size information." (2.2 Blind Source Extraction)
- **AIPS** : Deconvolving Gaussian component sizes with the clean beam via the DECONV.FOR module in PyBDSF  
  > "the deconvolution follows the Astronomical Image Processing System (AIPS; Greisen 2002) `DECONV.FOR` module" (2.2. Blind Source Extraction)
- **getpix** : Aperture photometry and pre-selecting candidate prior sources for GALFIT fitting  
  > "We refer to this aperture photometry as the getpix method hereafter" (2.4. Prior Source Fitting); "This first getpix step also provides guidance for the prior source fitting using galfit (Peng et al. 2002, 2010) in the next step." (2.4. Prior Source Fitting)
- **GALFIT** : Iterative prior-based source fitting on ALMA continuum images  
  > "This first getpix step also provides guidance for the prior source fitting using galfit (Peng et al. 2002, 2010) in the next step." (2.4. Prior Source Fitting)
- **GILDAS** : uv-plane source fitting with uv_fit and uv-plane spectral line extraction  
  > "task to fit Gaussian and/or point-source models then compare the total flux with those measured from the image-plane galfit and PyBDSF fitting." (2.6 Comparison to uv-plane Source Fitting Results); "The line search is done in the _uv_ -plane adapting the methodology of Silverman et al. (2015b) and D. Liu et al. (2019, in preparation), with CASA and GILDAS." (4.5. Correcting significant contribution from emission lines)
- **scikit-learn** : Gaussian Process supervised machine-learning classification of multi-wavelength counterpart associations  
  > "For this supervised machine learning task, we use the Python scikit-learn package (Pedregosa et al. 2011)." (4.2. Examining counterpart association)
- **MAGPHYS** : Multi-wavelength UV-to-mm/radio SED fitting at fixed prior redshift to derive galaxy physical properties  
  > "We use MAGPHYS (da Cunha et al. 2008, 2015) [22] for the SED fitting, as it has rich stellar SED libraries" (4.4 SED fitting)
- **MAGPHYS+photo-z** : Photometric redshift SED fitting to validate prior redshifts and estimate M_* and SFR uncertainties including redshift errors  
  > "we adopt the recently developed photo- _z_ version of the MAGPHYS code (MAGPHYS+photo-z; A. Battisti et al. in prep.)." (4.4. SED fitting)
- **Crab.Toolkit.michi2** : Experimental multi-component stellar+AGN chi-square SED fitting for problematic AGN outliers  
  > "To verify the degeneracy between age and attenuation, we ran some additional SED fitting with our multi-component _χ_ [2] fitting code under development" (E. PROBLEMATIC SED FITTING CASES); "It is still in the experimental phase but is available at http://github.com/1054/Crab.Toolkit.michi2." (E. PROBLEMATIC SED FITTING CASES)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total number of ALMA continuum images processed (v20180102) | 1534 | not stated | dimensionless | 1 | from a parent sample 823 galaxies with at least one ALMA detection in 1534 ALMA archive images (from 142 ALMA projects) available for the COSMOS field; for the COSMOS field 1534 pointings covering an area of 164 arcmin [2] have been publicly available since Jan. 2nd, 2018 |
| Total primary beam area covered (v20180102) | 164 | not stated | arcmin^2 | 1 | The sum of primary beam area of these observations reaches 164 arcmin [2] as of Jan. 2nd, 2018 |
| Blind source extraction catalog detections (S/N_peak > 5.40) | 939 | not stated | dimensionless | 2 | Blind-photometry catalog 939 _· · ·_; the final catalogs (version `v20180201` ) contain 939 sources above a peak flux S _/_ N peak = 5 _._ 40 for the blindly detected sources (with a cumulative spurious fraction of _∼_ 8%) |
| Prior source fitting catalog detections (S/N_peak > 4.35) | 1027 | not stated | dimensionless | 3 | Prior-photometry catalog 1027 _· · ·_; and 1027 sources above a peak flux S _/_ N peak = 4 _._ 35 for the prior selected sources (with a cumulative spurious fraction of _∼_ 12%). |
| Cumulative spurious fraction for blind catalog (S/N_peak > 5.40) | <8 | not stated | % | 2 | and the cumulative spurious fractions are _<_ 8% and _<_ 12% for the blind- and prior-selected samples, respectively |
| Cumulative spurious fraction for prior catalog (S/N_peak > 4.35) | <12 | not stated | % | 3 | and the cumulative spurious fractions are _<_ 8% and _<_ 12% for the blind- and prior-selected samples, respectively |
| Cumulative completeness for blind catalog (S/N_peak > 5.40) | >92 | not stated | % | 4 | The corresponding differential completenesses at those thresholds are 57% and 98%, and the cumulative ones are as high as _>_ 92% and _>_ 99%, respectively |
| Cumulative completeness for prior catalog (S/N_peak > 4.35) | >99 | not stated | % | 4 | The corresponding differential completenesses at those thresholds are 57% and 98%, and the cumulative ones are as high as _>_ 92% and _>_ 99%, respectively |
| Mean log10(S_PyBDSF / S_GALFIT) flux difference | -0.013 | 0.10 | dex | 3 | Histogram of the flux difference on a logarithmic scale, log 10 ( _S_ PyBDSF _/S_ GALFIT ). The mean is _−_ 0 _._ 013 with a standard deviation of 0.10 dex. |
| Median log10 difference between blind photometry and uv_fit flux densities | 0.015 | 0.08 | dex | 3 | a logarithmic scale) has a median of 0.015 dex and scatter of 0.08 dex. |
| Median log10 difference between prior photometry and uv_fit flux densities | -0.005 | 0.13 | dex | 3 | The difference between prior photometry and `uv_fit` flux densities has a median of -0.005 dex and scatter of 0.13 dex |
| Gaussian Process counterpart association validation accuracy | 96.5 | not stated | % | 5 | Running our trained model on the validation sample gave an accuracy of _∼_ 96 _._ 5%. |
| Number of galaxies in final robust galaxy catalog | 676 | not stated | dimensionless | 7 | Final galaxy catalog (Sect. 5) _[d]_ 676 _· · ·_; The final galaxy catalog (version `20180201` ) contains 676 galaxies in the range of _z_ = 0 _._ 25 _−_ 5 _._ 67, _M_ _∗_ = 3 _×_ 10 [7] _−_ 1 _._ 9 _×_ 10 [12] M _⊙_ and SFR = 0 _._ 02 _−_ 4000 M _⊙_ yr _[−]_ [1] . |
| Redshift range of final galaxy catalog | 0.25-5.67 | not stated | dimensionless | 7 | The final galaxy catalog (version `20180201` ) contains 676 galaxies in the range of _z_ = 0 _._ 25 _−_ 5 _._ 67, _M_ _∗_ = 3 _×_ 10 [7] _−_ 1 _._ 9 _×_ 10 [12] M _⊙_ and SFR = 0 _._ 02 _−_ 4000 M _⊙_ yr _[−]_ [1] . |
| Stellar mass range of final galaxy catalog | 3e7-1.9e12 | not stated | M_sun | 7 | The final galaxy catalog (version `20180201` ) contains 676 galaxies in the range of _z_ = 0 _._ 25 _−_ 5 _._ 67, _M_ _∗_ = 3 _×_ 10 [7] _−_ 1 _._ 9 _×_ 10 [12] M _⊙_ and SFR = 0 _._ 02 _−_ 4000 M _⊙_ yr _[−]_ [1] . |
| Star formation rate range of final galaxy catalog | 0.02-4000 | not stated | M_sun yr^-1 | 7 | The final galaxy catalog (version `20180201` ) contains 676 galaxies in the range of _z_ = 0 _._ 25 _−_ 5 _._ 67, _M_ _∗_ = 3 _×_ 10 [7] _−_ 1 _._ 9 _×_ 10 [12] M _⊙_ and SFR = 0 _._ 02 _−_ 4000 M _⊙_ yr _[−]_ [1] . |

## Qualitative findings

- Flux bias parameterization at low S/N depends strongly on the input mock source population of Monte Carlo simulations due to resolution bias, making physically motivated (PHYS) simulations more realistic than uniform full-parameter-space (FULL) simulations.  
  > "Here, we also found that the flux bias parameterization strongly depends on the input mock source populations of the MC simulation as demonstrated below." (3.1.1. Flux bias in the PyBDSF photometry); "Therefore, in our ALMA (sub-)mm data, the real galaxy angular size distribution should be dominated by small sources, i.e., it is better described by the “PHYS” simulation rather than the “FULL” simulation." (3.1.1. Flux bias in the PyBDSF photometry)
- Condon (1997) Gaussian fit error prescriptions capture the primary dependence on Theta_beam but miss a weak dependence on S/N_peak, overestimating errors by ~40% for large high-S/N sources in FULL simulations and underestimating by ~15% for small high-S/N sources in PHYS simulations.  
  > "Fig. 13 indeed shows a strong dependency on Θ beam but also indicates a weak dependency on S _/_ N peak ." (3.1.3. Flux error estimation for PyBDSF photometry); "However, the “FULL” simulation panel indicates that Condon (1997) errors are overestimated by about 40% for large, high-S _/_ N peak sources; while the “PHYS” simulation panel indicates that Condon (1997) errors are underestimated by about 15% for small, high-S _/_ N peak sources." (3.1.3. Flux error estimation for PyBDSF photometry)
- Iterative MAGPHYS SED fitting without an AGN component yields stellar masses in good agreement with SED3FIT (which includes an AGN component), even for classified AGNs, except for a few extreme mid-IR AGN outliers.  
  > "Our current multi-run, iterative MAGPHYS SED fitting, although without an AGN component, achieves in general good agreement with SED fitting that includes an AGN component." (4.6. Obtaining galaxy properties from SED fitting)
- Galaxy-galaxy strong gravitational lensing (magnification > 2) is negligible in the A3COSMOS sample, affecting only ~3 expected sources.  
  > "Scaling to our galaxy catalog source number of 823, only three strongly ( _µ_ _>_ 2) lensed sources are expected." (4.9. The effect of galaxy-galaxy gravitational lensing); "Therefore, we conclude that strong lensing is not affecting the properties of most of our galaxies." (4.9. The effect of galaxy-galaxy gravitational lensing)

## Claim tuples

- H: Public PI-led ALMA archival observations in the COSMOS field can be homogeneously imaged and mined with complementary blind and prior-based photometry pipelines to produce consistent, accurate continuum flux densities. | E: Imaged 1534 archival pointings with CASA (robust=2), extracted sources using PyBDSF (blind) and GALFIT (prior-based), and compared fluxes against each other, GILDAS uv_fit on 301 pointings, and getpix aperture photometry. | R: 96% of common sources between PyBDSF and GALFIT agree within 3 sigma (mean log10 ratio -0.013 +/- 0.10 dex), and median offsets relative to uv_fit are 0.015 dex (blind) and -0.005 dex (prior). | F: Image-plane blind and prior-based continuum photometries are mutually consistent and agree well with uv-plane fitting and aperture photometry. | **supported**
- H: The prior distribution of source flux densities and sizes assumed in Monte Carlo simulations significantly impacts derived flux bias corrections and error estimates. | E: Performed two MC simulations on 150+ representative ALMA residual maps: a uniform grid simulation (FULL) and a physically motivated simulation (PHYS) based on empirical SMFs, MS relations, and galaxy size evolution. | R: At low S/N_peak and small recovered sizes, the FULL simulation shows much smaller flux boosting than the PHYS simulation due to resolution bias from abundant simulated large, low-S/N sources; applying PHYS corrections yields normalized residual histograms matching a unit Gaussian. | F: Realistic input galaxy distributions (PHYS) are required to properly correct flux biases and re-estimate flux errors in ALMA continuum photometry. | **supported**
- H: Multi-wavelength counterpart association for ALMA detections can be automated using supervised machine learning to replace manual visual inspection. | E: Measured positional separation, S/N, surface brightness extension (Ext.), crowdedness, and clean parameters on HST i-band, UltraVISTA Ks, IRAC 3.6 um, and VLA 3 GHz cutouts for 1027 sources, training a scikit-learn Gaussian Process classifier on 60% of visually classified sources. | R: The GP classifier achieved ~96.5% accuracy on the 40% validation set and 97% overall agreement with visual classifications, flagging 36 unreliable counterpart outliers. | F: The trained Gaussian Process classifier reliably automates counterpart association quality assessment for ALMA detections. | **supported**
- H: Iterative MAGPHYS SED fitting (with energy balance and ALMA continuum constraints, iterating with and without 24 um data) provides reliable stellar masses even without an explicit AGN template component. | E: Compared MAGPHYS stellar masses against SED3FIT stellar masses (which include an AGN component) from Delvecchio et al. (2017) for 396 common galaxies, including 158 classified AGNs. | R: 391 of 396 galaxies agree within 3 sigma, with only 5 outliers outside the 3 sigma envelope. | F: Multi-run MAGPHYS SED fitting with ALMA continuum constraints yields robust stellar masses for the vast majority of galaxies, including AGN hosts. | **supported**

## Reasoning

- Why this data: The COSMOS field has the richest, deepest multi-wavelength datasets over 2 deg^2, and accumulated public PI-led ALMA observations cover 164 arcmin^2, exceeding the areal coverage of any contiguous ALMA deep field survey at all sensitivities.  
  > "We limit our selection to within the COSMOS field (R.A. = 10:00:28.6, decl. = +02:12:21.0, J2000; Scoville et al. 2007) because it is one of the deep fields with the richest, deepest multiwavelength datasets" (2. DATA AND PHOTOMETRY); "Given that the ALMA archival data in the COSMOS field alone cover a larger cumulative area at all sensitivities, a systematic mining of the ALMA archive is strongly motivated." (2. DATA AND PHOTOMETRY)
- Why this method: Combining blind source extraction (PyBDSF) and prior-based fitting (GALFIT) reaches deeper detection limits while identifying blended/inconsistent sources; physically-motivated MC simulations properly account for resolution and flux boosting biases.  
  > "In addition to the blind source extraction, we utilize known source positions as a prior for the source fitting. This technique allows for deeper detection limits and lowers the spurious source fraction." (2.3. Prior Source Master Catalog); "With both PyBDSF and prior-based galfit photometry, we not only obtain accurate independent fluxes which agree very well but also identify those few (0.5% [12] ) sources which suffer from source multiplicity/blending issues." (2.5 Comparing Blind Extraction and Prior Fitting)
- Alternative: Selecting the final sample with a total flux S/N threshold was rejected in favor of a constant S/N_peak threshold because completeness depends strongly on source size for total flux S/N.  
  > "Given our finding that completeness shows an obvious dependency on source sizes, if selecting a sample with a total flux S _/_ N threshold, the sample will have different completeness for different sizes. But when selecting with a constant S _/_ N peak threshold, the sample will have a homogeneous completeness." (3.2. Completeness)
- Alternative: Using the uniform full-parameter-space (FULL) simulation for final flux bias correction was rejected in favor of the physically-motivated (PHYS) simulation because FULL underestimates flux boosting at low S/N.  
  > "We choose the “PHYS” simulation for the final correction, considering the discussion in the previous sections, i.e., “PHYS” simulation is more representative of our real data. Note that using “FULL” simulation would underestimate the flux bias correction" (3.1.5. Final Corrections)
- Alternative: Direct blanking of line-contaminated channels before continuum imaging was rejected in favor of post-facto empirical line prediction and subtraction to avoid massive data volume, analysis time, and dataset inhomogeneity.  
  > "Direct blanking of channels affected by line emission before construction of the continuum image would require either a good a-priori knowledge of the redshift or dedicated line searches (that are not part of this project) as well as special treatment of each source present in a single pointing." (4.5. Correcting significant contribution from emission lines)
- How they decided it was enough: S/N_peak thresholds (5.40 for blind, 4.35 for prior) were chosen where the differential spurious fraction reaches 50%, keeping cumulative spurious fractions below 8-12% and cumulative completeness above 92-99%.  
  > "These thresholds are selected such that the differential spurious fractions are both 50% at the applied S _/_ N peak cut level, and the cumulative spurious fractions are _<_ 8% and _<_ 12% for the blind- and prior-selected samples, respectively" (4.1. Combining the two photometric catalogs)
- Limitation (authors): The final galaxy catalog has an undetermined selection function and is not complete in cosmic comoving volume, stellar mass, or SFR due to inhomogeneous PI-led targets.  
  > "we provide robust information on redshift, stellar mass and star formation rate for _∼_ 700 galaxies at redshifts 0.5-6 in the COSMOS field (with undetermined selection function)." (abstract); "we caution that this catalog is not complete in cosmic comoving volume, stellar mass or SFR." (6. Summary)
- Limitation (authors): Very high angular resolution ALMA images (synthesized beam < 0.1 arcsec, <=1% of data) and the AzTEC-3 mosaic project are excluded because the photometry pipelines are optimized for marginally resolved sources.  
  > "(but excluded very long baseline data with a synthesized beam _<_ 0 _._ 1 _[′′]_ ; see Sect. 2.1; and the only one mosaic project on the AzTEC-3 protocluster)." (2. DATA AND PHOTOMETRY); "Therefore, these ≲ 1% very high resolution ( _θ_ Maj _,_ beam _<_ 0 _._ 1 _[′′]_ ) images are excluded from our analysis." (2.1. ALMA Continuum Images)
- Limitation (authors): Visibility data for the same source taken at the same frequency across different ALMA projects are not combined.  
  > "Currently, data for the same source taken at the same frequency arising from different projects are not combined." (2.1. ALMA Continuum Images)
- Limitation (authors): 26% of ALMA detections (215 galaxies, including 119 blind-only sources and Ks-dropouts without optical/near-IR prior redshifts) are excluded from the final galaxy property catalog due to insufficient optical/near-IR constraints.  
  > "As 26% of these galaxies do not have sufficient optical/near-IR data, i.e., not in the Laigle et al. (2016) catalog, it is not possible to obtain reliable stellar masses for them." (4.1. Combining the two photometric catalogs)
- Limitation (authors): Dust masses are omitted from the released catalog because MAGPHYS can underestimate dust masses in post-starburst galaxy mergers.  
  > "Therefore, we do not provide dust masses in our final catalog and defer this to later work (our Paper II)." (4.6. Obtaining galaxy properties from SED fitting)
- Limitation (authors): At primary beam attenuation < 0.3, Gaussian primary beam approximations and frequency dependence across the 16 GHz sideband span introduce instrumental systematics.  
  > "We attribute the slight drop below _∼_ 0 _._ 3 to the fact that instrumental systematics are likely becoming more prominent" (2.8. Inverted-image Fitting and the Fraction of Spurious Detection)
- Caveat (inferred, ours): Aggregating all spectral windows into continuum images without prior line flagging means any unpredicted or anomalously bright emission line (or line in a source with an inaccurate photo-z) directly biases the continuum flux density.
- Caveat (inferred, ours): Using a single scalar primary beam attenuation factor evaluated at the source center can bias total flux measurements for extended sources located far from the phase center where the primary beam gradient is steep.
- Caveat (inferred, ours): Training and validating the Gaussian Process counterpart classifier on visual inspections of the same 1027-source dataset risks overfitting to the specific depth and resolution distribution of v20180102.

## Reproducibility

- Data public (paper): Yes, raw ALMA data are from the public ALMA archive and processed continuum images and catalogs are publicly released at IPAC/IRSA.  
  > "The ALMA photometric measurements and galaxy properties are released publicly within our blind-extraction, prior-fitting and galaxy property catalogs, plus the images." (abstract); "The catalogs are available from the COSMOS archive at IPAC/IRSA and in electronic form from the journal." (5. Data Products)
- Products in archive: All PBA-corrected and uncorrected continuum images and three catalogs (blind photometry, prior photometry, galaxy properties) are hosted on the COSMOS archive at IPAC/IRSA.  
  > "The catalogs are available from the COSMOS archive at IPAC/IRSA and in electronic form from the journal. Further, the ALMA continuum images are also provided via the COSMOS archive." (5. DATA PRODUCTS)
- Code: Experimental multi-component SED fitting code Crab.Toolkit.michi2 released on GitHub (http://github.com/1054/Crab.Toolkit.michi2); A3COSMOS project page at https://sites.google.com/view/a3cosmos.  
  > "https://sites.google.com/view/a3cosmos" (1. INTRODUCTION); "It is still in the experimental phase but is available at http://github.com/1054/Crab.Toolkit.michi2." (E. PROBLEMATIC SED FITTING CASES)
- Missing: Internal COSMOS spectroscopic redshift compilation catalog by M. Salvato et al. (version Sept. 1st, 2017) and unpublished SPLASH IRAC supplementary catalog (I. Davidzon, priv. comm.)
- Missing: Automated A3COSMOS wrapper scripts for running GALFIT, getpix, and the 2D flux bias/error lookup tables from the PHYS simulation
- Missing: Trained scikit-learn Gaussian Process model file and visual classification training labels for counterpart association
- Missing: Exact list of <10% continuum pointings where manual baseline flagging or robust=0.5 was applied during imaging
- Data volume (inferred): ~5-15 TB for raw/calibrated Measurement Sets of 52 ALMA projects (1534 pointings); ~10-50 GB for the released continuum FITS images and catalogs
- Score (inferred): 78/5, All raw ALMA data, calibrated continuum FITS images, and final photometry/property catalogs are publicly archived at IRSA, and the imaging, source extraction, simulation, and SED fitting recipes are thoroughly documented; however, full end-to-end reproduction from scratch is hindered by reliance on two internal COSMOS catalogs (Salvato spec-z compilation and SPLASH supplementary catalog), unstated per-image manual flagging choices (<10% of maps), and unreleased pipeline wrapper scripts/lookup tables.
- Rediscovery candidate: yes, Both the raw ALMA archival visibilities and the released continuum FITS images are public, the core software tools (CASA, PyBDSF, GALFIT, MAGPHYS) are standard and explicitly parameterized, and the catalog summary statistics and cross-method comparisons provide clear quantitative benchmarks.

## Links

- Method: Condon (1997) (Mathematical prescription for 2D Gaussian fitting parameter uncertainties in correlated noise)
- Method: Mohan & Rafferty (2015) (PyBDSF blind source extraction and Gaussian fitting code)
- Method: Peng et al. (2002, 2010) (GALFIT 2D image fitting code used for prior-based photometry)
- Method: Scoville et al. (2014, 2016, 2017) (Concentric aperture photometry (getpix) method and detection thresholds)
- Method: da Cunha et al. (2008, 2015) (MAGPHYS UV-to-mm energy-balance SED fitting code)
- Method: Liu et al. (2018); Jin et al. (2018) (Super-deblended FIR/mm photometry and IR SED modeling used in PHYS simulations)
- Companion: Paper II; D. Liu et al. 2019, submitted to ApJ. (Companion paper using the A3COSMOS catalog to study the cosmic evolution of molecular gas fraction and gas depletion time)
- Related: COSMOS
- Related: A3COSMOS
- Related: UltraVISTA
- Related: SPLASH
- Related: VLA-COSMOS
- Related: PEP

## Checks

```json
{
 "quotes": 223,
 "quotes_ok": 223,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 15,
 "unsupported_facts": 0,
 "project_codes": 39,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2011.0.00097.S",
  "2012.1.00076.S",
  "2012.1.00952.S",
  "2013.1.00092.S",
  "2013.1.00276.S",
  "2013.1.00884.S",
  "2015.1.00055.S",
  "2015.1.00260.S",
  "2015.1.00568.S",
  "2015.1.00853.S",
  "2015.1.01105.S",
  "2015.1.01212.S",
  "2016.1.00624.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 16,
 "numeric_problems": 0,
 "fill": {
  "facts": 126,
  "stated": 111,
  "rate": 0.881
 },
 "evidence_ok": true
}
```
