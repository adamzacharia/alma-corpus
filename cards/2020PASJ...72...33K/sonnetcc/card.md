# Deeply cooled core of the Phoenix galaxy cluster imaged by ALMA with the Sunyaev-Zel'dovich effect

`2020PASJ...72...33K` | Publications of the Astronomical Society of Japan 2020 | first author: Kitayama, Tetsu | arXiv: 2001.11239 | DOI: 10.1093/pasj/psaa009

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: galaxy_clusters_and_sz
- Question: How much thermal gas is cooling to low temperatures in the Phoenix cluster core, probed with an ALMA SZE image combined with Chandra X-ray data independent of the X-ray spectrum  
  > "One of the key questions on the nature of the Phoenix cluster is how much thermal gas is in fact cooling to sufficiently low temperatures." (Introduction); "It is hence crucial to explore the physical states of the gas by other independent methods." (Introduction)
- Target **SPT-CL J2344-4243 (Phoenix galaxy cluster)**: coordinates _not stated_; z/distance z = 0.597  
  > "The Phoenix galaxy cluster, SPT-CL J2344-4243, at redshift $z=0.597$" (Introduction); "the angular size of 1$''$ corresponds to the physical size of 4.67 $h^{-1}$kpc at the source redshift $z=0.597$" (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.00894.S
- bands: Band 3; four continuum bands centered at 85, 87, 97, 99 GHz (overall central frequency 92 GHz)  
  > "All the data were taken at four continuum bands centered at 85, 87, 97, and 99 GHz, yielding the overall central frequency of 92 GHz with an effective bandwidth of 7.5 GHz." (Observations and data reduction); "by the Atacama Large Millimeter/submillimeter Array (ALMA) in Band 3" (abstract)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: effective bandwidth 7.5 GHz  
  > "yielding the overall central frequency of 92 GHz with an effective bandwidth of 7.5 GHz" (Observations and data reduction)
- arrays: ALMA 12-m and 7-m arrays  
  > "SPT-CL J2344–4243 was observed by the 12-m and 7-m arrays of ALMA" (Observations and data reduction)
- configurations: compact configurations; 12-m: 4 execution blocks, 7-m: 15 execution blocks  
  > "Compact configurations were adopted" (Observations and data reduction); "The observations were executed in 4 and 15 separate blocks for the 12-m and 7-m arrays, respectively." (Observations and data reduction)
- baselines: 3.7-145 klambda (12-m), 2.1-15.6 klambda (7-m)  
  > "to cover the baseline ranges of 3.7–145 k$\lambda$ and 2.1–15.6 k$\lambda$ for the 12-m and 7-m arrays, respectively" (Observations and data reduction)
- angular resolution: ~2 arcsec native; 2.25 x 1.92 arcsec FWHM (12-m + 7-m) unsmoothed; 5 arcsec smoothed for display  
  > "They yielded the angular resolution and the maximum recoverable scale of $\sim 2''$ and $\sim 60''$, respectively." (Observations and data reduction); "quantitative analysis in this paper was done on the unsmoothed image with $2.25'' \times 1.92''$ FWHMs" (The Sunyaev-Zel’dovich effect)
- max recoverable scale: ~60 arcsec  
  > "They yielded the angular resolution and the maximum recoverable scale of $\sim 2''$ and $\sim 60''$, respectively." (Observations and data reduction)
- sensitivity: 0.025 mJy/beam rms at 5 arcsec resolution (theta < 45 arcsec); 0.0122 mJy/beam 1 sigma at native resolution (12-m + 7-m)  
  > "The rms noise level measured on the difference map smoothed to the $5''$ resolution is 0.025 mJy/beam at $\theta < 45''$." (The Sunyaev-Zel’dovich effect); "Average 1$\sigma$ noise \[mJy/beam\] | 0.0123 | 0.0144 | 0.0714 | 0.0122" (Table 2)
- time on source: 3.21 hr (12-m), 8.06 hr (7-m)  
  > "Total on-source time \[hr\] | 3.21 | 8.06" (Table 1)
- observing dates: March 17-19, 2016 (12-m); May 3 - June 12, 2016 (7-m)  
  > "Date | March 17 – 19, 2016 | May 3 – June 12, 2016" (Table 1)
- pi or archival as stated: _not stated_
- Other facility **Chandra ACIS-I**: X-ray data (12 ObsIDs, total exposure 551.5 ksec) combined with the ALMA SZE image  
  > "we extracted the X-ray data of the Phoenix cluster taken by Chandra ACIS-I" (4.1 Comparison to X-ray data); "The total exposure time is 551.5 ksec." (4.1 Comparison to X-ray data)
- Other facility **ATCA**: 18 GHz detections of the compact sources, discussed in a separate paper  
  > "These sources are also detected at 18 GHz by ATCA and their properties are discussed in detail in a separate paper (cite: Akahori19)." (3.1 Compact sources)
- Other facility **South Pole Telescope (SPT)**: first identification of the cluster via the SZE (angular resolution >1 arcmin)  
  > "While the cluster was first identified via the SZE by the South Pole Telescope (SPT) (cite: Carlstrom11; Williamson11)" (Introduction)
- External data: M500 = 8.8e14 h^-1 Msun and r500 = 0.92 h^-1 Mpc of the Phoenix cluster  
  > "assuming $M_{500} = 8.8 \times 10^{14} h^{-1} M_{\odot}$ and $r_{500} = 0.92 h^{-1}$Mpc at $z=0.597$ for the Phoenix cluster" (4.3 Compton y-parameter map and the inner pressure profile) [from (cite: McDonald12)]
- External data: Mean radial pressure profiles of local cool core clusters, used as comparison  
  > "We find that the inner pressure profile of the Phoenix cluster is in good agreement with the expectation from the local cool core clusters by (cite: Arnaud10)" (4.3 Compton y-parameter map and the inner pressure profile) [from (cite: Arnaud10)]
- External data: Generalized NFW pressure profile form, integrated along the line of sight for the comparison profiles  
  > "The mean radial pressure profiles are computed by integrating along the line-of-sight the generalized NFW profile (cite: Nagai07)" (4.3 Compton y-parameter map and the inner pressure profile) [from (cite: Nagai07)]
- External data: Mean temperature profiles of local and distant cool core clusters, scaled with kT500 = 12.6 keV from the X-ray scaling relation  
  > "Also plotted for reference in figure [13](#fig-tdeproj) are the mean profiles of local and distant cool core clusters (cite: Vikhlinin06; McDonald14b)" (4.4 Deprojected electron temperature and density); "using the average temperature within $r_{500}$ of this cluster, $kT_{500}=12.6$ keV, expected from the X-ray scaling relation by (cite: Reichert11)" (4.4 Deprojected electron temperature and density) [from (cite: Vikhlinin06; McDonald14b); scaling relation (cite: Reichert11)]
- External data: Best-fit density profiles of Abell 2029 and Abell 1795  
  > "overlaid are the best-fit density profiles by (cite: Vikhlinin06) of typical local cool core clusters, Abell 2029 and Abell 1795" (4.4 Deprojected electron temperature and density) [from (cite: Vikhlinin06)]
- External data: Galactic hydrogen column density 1.52e20 cm^-2  
  > "the Galactic hydrogen column density toward the Phoenix cluster is $1.52 \times 10^{20}$ cm$^{-2}$ (cite: Kalberla05)" (4.1 Comparison to X-ray data) [from (cite: Kalberla05)]
- External data: Central galaxy stellar mass ~3e12 Msun  
  > "$\sim 3 \times 10^{12} M_\odot$ in the central galaxy of the Phoenix cluster (cite: McDonald12; McDonald13)" (4.5 How much gas is cooling in the Phoenix cluster?) [from (cite: McDonald12; McDonald13)]
- External data: Mass deposition rate ~2000 Msun/yr indicated by X-ray data  
  > "$\dot{M}_{\rm cool} \sim 2000 ~M_\odot$ yr$^{-1}$ as indicated by the X-ray data (e.g., (cite: McDonald13; Ueda13))" (4.5 How much gas is cooling in the Phoenix cluster?) [from (cite: McDonald13; Ueda13)]
- External data: Mass deposition rate 130-480 Msun/yr for gas below 2 keV  
  > "$\dot{M}_{\rm cool} = 130-480~M_\odot$ yr$^{-1}$ for the gas below 2 keV (cite: Pinto18)" (4.5 How much gas is cooling in the Phoenix cluster?) [from (cite: Pinto18)]
- External data: ALMA absolute flux calibration uncertainty of 6%  
  > "the absolute calibration of ALMA (6%: (cite: Kitayama16))" (4.3 Compton y-parameter map and the inner pressure profile) [from (cite: Kitayama16)]
- Simulation/model as data: Imaging simulations built from the X-ray pseudo pressure map normalised to peak Compton y of 8e-4 (also 4e-4 and 12e-4), observed with simobserve  
  > "we performed imaging simulations using the X-ray pseudo pressure map" (4.2 Imaging simulations); "we also examined the cases of $y_{\rm peak}=4 \times 10^{-4}$ and $12 \times 10^{-4}$." (4.2 Imaging simulations)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 5.6.1 (stated for imaging)  
  > "Imaging was done with the Common Astronomy Software Applications package (CASA: (cite: McMullin07)) version 5.6.1." (Observations and data reduction)
- pipeline version: _not stated_
- archive products used as is: QA2 visibility data used  
  > "we used the visibility data produced by the second stage of ALMA’s Quality Assurance process (QA2)" (Observations and data reduction)
- flux calibrator: Neptune (12-m); Neptune, Uranus (7-m)  
  > "Flux calibrator | Neptune | Neptune, Uranus" (Table 1)
- flux scale uncertainty: 6% (absolute calibration of ALMA, from Kitayama et al. 2016)  
  > "the absolute calibration of ALMA (6%: (cite: Kitayama16))" (4.3 Compton y-parameter map and the inner pressure profile)
- self calibration: _not stated_

### Imaging

- task: CASA tclean (joint mosaic, multi-frequency synthesis)  
  > "using the CASA task *tclean*" (3.2 The Sunyaev-Zel’dovich effect); "We adopted the multi-frequency synthesis mode in joint mosaic imaging." (Observations and data reduction)
- deconvolver: Multi-Scale CLEAN  
  > "The source-subtracted visibility data were deconvolved with the Multi-Scale CLEAN algorithm (cite: Cornwell08; Rich08; Steeb19)" (3.2 The Sunyaev-Zel’dovich effect)
- weighting robust: natural weighting  
  > "Natural weighting was used" (Observations and data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: circular mask radius 42 arcsec; flux threshold 0.024 mJy; loop gain 0.05  
  > "We used a circular mask region with radius $\theta = 42''$, a flux threshold of 0.024 mJy, and a loop gain of 0.05." (3.2 The Sunyaev-Zel’dovich effect)
- multiscale scales: [0, 4, 8, 16, 32, 64] arcsec Gaussian FWHMs  
  > "We adopted \[0, $4''$, $8''$, $16''$, $32''$, $64''$\] as the FWHMs of the Gaussian components used in Multi-Scale CLEAN" (3.2 The Sunyaev-Zel’dovich effect)
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: all images corrected for primary beam attenuation  
  > "all the images presented were corrected for primary beam attenuation" (Observations and data reduction)
- array combination: 12-m and 7-m visibilities imaged jointly as a mosaic  
  > "We adopted the multi-frequency synthesis mode in joint mosaic imaging." (Observations and data reduction); "the deconvolved SZE image created from the visibility data taken by the 12-m and 7-m arrays" (3.2 The Sunyaev-Zel’dovich effect)
- smoothing: smoothed to 5 arcsec FWHM for display; quantitative analysis on unsmoothed image  
  > "The image has been smoothed to an effective beam size of $5''$ FWHM for display purposes" (3.2 The Sunyaev-Zel’dovich effect)
- final beam: 2.25 x 1.92 arcsec FWHM (12-m + 7-m, unsmoothed)  
  > "quantitative analysis in this paper was done on the unsmoothed image with $2.25'' \times 1.92''$ FWHMs" (3.2 The Sunyaev-Zel’dovich effect)
- final rms: 0.025 mJy/beam at 5 arcsec resolution (theta < 45 arcsec)  
  > "The rms noise level measured on the difference map smoothed to the $5''$ resolution is 0.025 mJy/beam at $\theta < 45''$." (3.2 The Sunyaev-Zel’dovich effect)

### Inherited from earlier work

- ALMA imaging procedure  
  > "The procedure was similar to (cite: Kitayama16)." (Observations and data reduction) [from (cite: Kitayama16)]
- Statistical error in each radial bin computed with equation (1) of the earlier paper  
  > "The statistical error in each bin is computed using equation (1) of (cite: Kitayama16)." (3.2 The Sunyaev-Zel’dovich effect) [from (cite: Kitayama16)]
- Linear relation between simulated output and input intensities  
  > "As in (cite: Kitayama16), we find that the simulation results on average follow the linear relation" (4.2 Imaging simulations) [from (cite: Kitayama16)]
- X-ray thermodynamic mapping with contour binning  
  > "As in (cite: Kitayama16), we performed X-ray thermodynamic mapping using the contour binning algorithm (cite: Sanders06)." (4.1 Comparison to X-ray data) [from (cite: Kitayama16); (cite: Sanders06)]
- AGN spectral model (obscured power law plus 6.4 keV iron line)  
  > "an iron fluorescent line at the rest-frame energy of 6.4 keV as in (cite: Ueda13)" (4.1 Comparison to X-ray data) [from (cite: Ueda13)]
- Additional photoelectric absorption by cool gas within the cluster  
  > "Following (cite: McDonald19), we also took into account additional photoelectric absorption by cool gas within the Phoenix cluster" (4.1 Comparison to X-ray data) [from (cite: McDonald19)]
- Equation-of-state analysis of observed perturbations  
  > "we applied the same method as in section 3.4 of (cite: Ueda18)" (4.1 Comparison to X-ray data) [from (cite: Ueda18)]
- Compact source naming  
  > "The assigned source names are the same as in (cite: Akahori19)" (3.1 Compact sources) [from (cite: Akahori19)]

### Not stated but needed to reproduce (our reading)

- Phase centre (target field centre) coordinates are blank in the text
- tclean image size, cell size, niter / number of minor cycles, gridder and phasecenter for the 7-pointing mosaic
- Calibration CASA/pipeline version and whether QA2 products were used unmodified or re-calibrated; any self-calibration
- Starting parameters, weighting and error treatment used in uvmodelfit; source positions are blank in the table
- Exact definition of how the difference-map noise was computed per pixel region and how the 5 arcsec smoothing was applied
- simobserve inputs: sky model construction from the pseudo pressure map, PWV values, and the Chandra-based map units used
- How the mean signal at the edge of the emission profile was determined when subtracting the offset
- Chandra reprocessing steps, region definitions and ACIS-I spectral fitting statistic; five-parameter initial values and fixed AGN parameter values
- Deprojection algorithm: optimiser, error propagation, shell geometry for the 0.7-2.0 keV X-ray brightness fit, and the covariance treatment between bins
- Code for deprojection and the relativistic SZ correction implementation is not named or released
- Choice of h = 0.7 for the deprojection versus h left free elsewhere

## Analysis recipe

1. **Fit and subtract compact sources in the uv plane**: Fit point-like and Gaussian models to 12-m visibilities at baselines >30 klambda with uvmodelfit, subtract in the uv plane before imaging  
  > "we determined their positions and flux densities by fitting with the CASA task *uvmodelfit* the 12-m array visibility data at baselines longer than 30k$\lambda$" (3.1 Compact sources); "Source identification and subtraction are done in the $uv$ plane and fully independent of the image synthesis method." (3.1 Compact sources)
   - software: CASA uvmodelfit
   - parameter: Four compact sources detected above 5 sigma  
  > "There are four compact sources detected by emission above the $5\sigma$ significance level in our target field." (3.1 Compact sources)
   - parameter: C2 modelled as elliptical Gaussian with major-to-minor axis ratio fixed at 0.05  
  > "We thus modeled this source by an elliptical Gaussian, fixing the major-to-minor axis ratio at 0.05" (3.1 Compact sources)
   - assumption: C3 and W modelled as point sources since consistent with the synthesized beam  
  > "As the shapes of sources C3 and W are consistent with the synthesized beam, they are modeled by point sources." (3.1 Compact sources)
   - fitting: _not stated_
   - validation: Residual long-baseline image after subtracting all sources is consistent with noise; results insensitive to assumed axis ratio  
  > "The residuals have the root mean square (rms) value of 0.0146 mJy/beam and are consistent with noise." (3.1 Compact sources); "We checked that the results are insensitive to the assumed value of the axis ratio as long as the minor axis remains negligible compared to the synthesized beam size." (3.1 Compact sources)
2. **Image the SZE decrement with 12-m + 7-m multi-scale CLEAN**: Deconvolve the source-subtracted 12-m + 7-m visibilities with Multi-Scale CLEAN in tclean using joint mosaic imaging, multi-frequency synthesis and natural weighting; measure noise on half-split difference maps  
  > "The source-subtracted visibility data were deconvolved with the Multi-Scale CLEAN algorithm (cite: Cornwell08; Rich08; Steeb19) using the CASA task *tclean*." (3.2 The Sunyaev-Zel’dovich effect); "dividing the data set in half, taking a difference between their dirty images, and dividing it by a factor 2 to correct for the reduction of the integration time" (Observations and data reduction)
   - software: CASA tclean
   - parameter: Scales [0, 4, 8, 16, 32, 64] arcsec FWHM  
  > "We adopted \[0, $4''$, $8''$, $16''$, $32''$, $64''$\] as the FWHMs of the Gaussian components used in Multi-Scale CLEAN" (3.2 The Sunyaev-Zel’dovich effect)
   - parameter: Mask radius 42 arcsec, threshold 0.024 mJy, loop gain 0.05  
  > "We used a circular mask region with radius $\theta = 42''$, a flux threshold of 0.024 mJy, and a loop gain of 0.05." (3.2 The Sunyaev-Zel’dovich effect)
   - fitting: _not stated_
   - validation: Scale choice described as optimal for maximal recovered flux and minimal residuals; results essentially unchanged with the CASA 5.6.0 Multi-Scale CLEAN modification  
  > "this is an optimal choice for the present target and assure maximal recovered flux as well as minimal residuals" (3.2 The Sunyaev-Zel’dovich effect); "We checked that the results of the present paper remain essentially unchanged by this modification as long as the Gaussian components are chosen to give maximal recovered flux and minimal residuals as described in the text." (Footnote 1)
3. **Extract Chandra X-ray spectra and compare with the SZE**: Contour-binned Chandra ACIS-I spectra (S/N 100) fitted with an ICM plus central AGN model in XSPEC; compare X-ray and SZE residual maps and estimate equation-of-state perturbations  
  > "As in (cite: Kitayama16), we performed X-ray thermodynamic mapping using the contour binning algorithm (cite: Sanders06)." (4.1 Comparison to X-ray data); "we defined subregions with nearly equal photon counts by adopting the signal-to-noise ratio (S/N) threshold of 100 (i.e., $\sim 10000$ counts) in the $0.7-7.0$ keV band" (4.1 Comparison to X-ray data)
   - software: CIAO 4.11, XSPEC 12.10.0e
   - parameter: Energy range 0.7-7.0 keV observed  
  > "We used the data at observed energies $E=0.7-7.0$ keV to minimize the effects of the ACIS contamination layer and the instrumental background" (4.1 Comparison to X-ray data)
   - parameter: Background from off-center region 3-5 arcmin from the central AGN  
  > "The backgrounds were estimated from the off-center region at $3' < r < 5'$ from the central AGN, where the ICM emission is negligible." (4.1 Comparison to X-ray data)
   - parameter: Five position-dependent free parameters (ICM temperature, metallicity, intrinsic absorber column, ICM and AGN normalisations)  
  > "there were in total five position-dependent free parameters in our spectral model" (4.1 Comparison to X-ray data)
   - parameter: Equation-of-state method of Ueda et al. 2018 with line-of-sight depth l = 100 kpc  
  > "we applied the same method as in section 3.4 of (cite: Ueda18)" (4.1 Comparison to X-ray data); "assuming the line-of-sight depth of $l=100$ kpc" (4.1 Comparison to X-ray data)
   - assumption: Collisional ionization equilibrium; Anders & Grevesse 1989 abundances  
  > "we assumed that the ICM is in collisional ionization equilibrium, the abundance ratio of elements heavier than helium is that of (cite: Anders89)" (4.1 Comparison to X-ray data)
   - assumption: Galactic NH = 1.52e20 cm^-2  
  > "the Galactic hydrogen column density toward the Phoenix cluster is $1.52 \times 10^{20}$ cm$^{-2}$ (cite: Kalberla05)" (4.1 Comparison to X-ray data)
   - assumption: Helium mass fraction Y = 0.25  
  > "We fixed the helium mass fraction at $Y=0.25$" (4.1 Comparison to X-ray data)
   - fitting: XSPEC spectral fitting; fit statistic reported as chi2/dof  
  > "Spectral fitting was done with XSPEC version 12.10.0e (cite: Arnaud96)." (4.1 Comparison to X-ray data)
   - validation: AGN emission checked to be consistent with the ACIS-I PSF and negligible beyond 5 arcsec; fit improves with intrinsic absorption  
  > "We also checked that the AGN emission is consistent with the point spread function (PSF) of ACIS-I" (4.1 Comparison to X-ray data)
4. **Simulate ALMA observations to calibrate missing flux**: Generate mock visibilities with simobserve from an X-ray pseudo-pressure model at four spectral windows, add noise, deconvolve as for real data, and fit I_out = c1 I_in + c0  
  > "Visibility data were then produced using the CASA task *simobserve* including both instrumental and atmospheric thermal noise in each spectral window." (4.2 Imaging simulations); "The mock visibility was deconvolved in the same way as the real data" (4.2 Imaging simulations)
   - software: CASA simobserve, CASA tclean
   - parameter: Four spectral windows at 85, 87, 97, 99 GHz with 1.875 GHz bandwidth each  
  > "We created model images separately at four spectral windows centered at 85, 87, 97, and 99 GHz with an effective bandwidth of 1.875 GHz each." (4.2 Imaging simulations)
   - parameter: Pointings, array configuration, hour angle, integration time and PWV matched to each execution block  
  > "The pointing directions, the array configuration, the hour angle, the total effective integration time, and the average precipitable water vapor were set to match those of each executing block of real observations." (4.2 Imaging simulations)
   - parameter: 10 noise realizations for each ypeak (4e-4, 8e-4, 12e-4)  
  > "For each value of $y_{\rm peak}$, we repeated the above procedure 10 times adopting different noise realizations." (4.2 Imaging simulations)
   - assumption: Pseudo pressure map normalised to ypeak = 8e-4, described as typical of massive cool core clusters; relativistic correction applied  
  > "which is a typical value for massive cool core clusters" (4.2 Imaging simulations); "A relativistic correction to the SZE intensity by (cite: Itoh04) was applied" (4.2 Imaging simulations)
   - fitting: Linear fit to the 10 realizations per ypeak with c1 common among ypeak values  
  > "where $c_1$ is assumed to be common among different values of $y_{\rm peak}$" (4.2 Imaging simulations)
   - validation: Simulated images reproduced by the linear relation with c1 close to unity; result consistent with the real image representing differential true intensity  
  > "confirms that the observed ALMA SZE image gives a reasonable representation of differential values of the true intensity (cite: Kitayama16)" (4.2 Imaging simulations)
5. **Derive the Compton y map and compare the inner pressure profile**: Divide ALMA image by c1 = 0.94, subtract mean signal at theta = 42 arcsec, apply relativistic correction with projected X-ray temperature, azimuthally average and compare with generalized NFW pressure profiles of cluster samples  
  > "the ALMA image was divided by the correction factor for the missing flux of 0.94" (4.3 Compton y-parameter map and the inner pressure profile); "the mean signal (consistent with zero) at $\theta = 42''$ is subtracted" (4.3 Compton y-parameter map and the inner pressure profile); "The mean radial pressure profiles are computed by integrating along the line-of-sight the generalized NFW profile (cite: Nagai07)" (4.3 Compton y-parameter map and the inner pressure profile)
   - parameter: Geometrically spaced bins, innermost 0-4 arcsec, size increasing by a factor 1.1  
  > "the bins are geometrically spaced with the inner-most bin at $0 < \theta < 4''$ and the size increasing by a factor of 1.1" (4.3 Compton y-parameter map and the inner pressure profile)
   - assumption: M500 = 8.8e14 h^-1 Msun, r500 = 0.92 h^-1 Mpc at z = 0.597  
  > "assuming $M_{500} = 8.8 \times 10^{14} h^{-1} M_{\odot}$ and $r_{500} = 0.92 h^{-1}$Mpc at $z=0.597$ for the Phoenix cluster" (4.3 Compton y-parameter map and the inner pressure profile)
   - fitting: _not stated_
   - validation: y map morphology consistent with X-rays; inner profile agrees with local cool core expectation  
  > "overall morphology of the Compton $y$-parameter map does not exhibit deviation from that of X-rays." (4.3 Compton y-parameter map and the inner pressure profile)
6. **Non-parametric deprojection of electron temperature and density**: Joint fit of SZE brightness (theta < 40 arcsec) and 0.7-2.0 keV X-ray brightness (theta < 100 arcsec) in spherical shells, varying T and ne per shell, with systematic errors added in quadrature; compared against an X-ray-only projct deprojection  
  > "Assuming spherical symmetry and $h=0.7$ for this particular purpose, we performed non-parametric deprojection of electron density $n_{\rm e}$ and temperature $T$" (4.4 Deprojected electron temperature and density); "using the model *projct* implemented in XSPEC version 12.10.0e (cite: Arnaud96)" (4.4 Deprojected electron temperature and density)
   - software: SPEX v3.0.5.00, XSPEC projct
   - parameter: Innermost bin 0-4 arcsec (0 < r < 26.7 kpc), size increasing by a factor 1.3  
  > "with the inner-most bin at $0 < \theta < 4''$ (corresponding to the deprojected spherical shell of $0 < r < 26.7$ kpc) and the size increasing by a factor of 1.3" (4.4 Deprojected electron temperature and density)
   - parameter: Systematic errors: ALMA flux calibration 6%, missing flux 0.24 uJy/arcsec^2, Chandra ACIS-I effective area 4%  
  > "Systematic errors from the flux calibration of ALMA (6%), the missing flux correction of the SZE (0.24 $\mu$Jy/arcsec$^2$), and the effective area of Chandra ACIS-I (4%)" (4.4 Deprojected electron temperature and density)
   - parameter: SZE modelled as incremental brightness relative to the bin at theta = 43.6 arcsec, with missing-flux factor 0.94 and temperature-dependent relativistic correction  
  > "we modeled and fitted the incremental brightness relative to the bin centered at $\theta=43.6''$" (4.4 Deprojected electron temperature and density); "the missing flux correction factor of 0.94 and the temperature-dependent relativistic correction were applied to the model brightness in each spherical shell" (4.4 Deprojected electron temperature and density)
   - assumption: Temperature at r > 250 kpc fixed at 15.8 keV from the X-ray spectral analysis  
  > "it was fixed at the projected mean value of 15.8 keV by the X-ray spectral analysis" (4.4 Deprojected electron temperature and density)
   - assumption: Metal abundance 0.35 Solar in SPEX emissivity  
  > "fixing the metal abundance at 0.35 times the Solar value" (4.4 Deprojected electron temperature and density)
   - assumption: Innermost-bin intrinsic NH either 6.7e21 cm^-2 or 0  
  > "the hydrogen column density in the inner-most bin was assumed to be either $N_{\rm H, int} =6.7 \times 10^{21}$ cm$^{-2}$ or $N_{\rm H, int} =0$" (4.4 Deprojected electron temperature and density)
   - fitting: Joint fit of SZE and X-ray volume-averaged brightness; optimiser and likelihood not stated  
  > "We then fitted the volume averaged brightness in each bin of the SZE at $\theta < 40''$ and of the 0.7–2.0 keV X-rays at $\theta < 100''$ together varying the temperature and the density in each spherical shell." (4.4 Deprojected electron temperature and density)
   - validation: Compared SZE+X-ray deprojection with X-ray-only deprojection; temperature profiles agree once intrinsic absorption is included  
  > "If intrinsic absorption is taken into account, the temperature profile from the latter deprojection method comes to a good agreement with that from the former." (4.4 Deprojected electron temperature and density)
7. **Derive entropy, cooling time and cool gas mass**: Compute K = kT ne^-2/3 and radiative cooling time from the deprojected profiles using SPEX emissivity; integrate gas mass at ~3 keV within r = 27 kpc and divide by mass deposition rates  
  > "the radiative cooling time, i.e., total thermal energy of the gas divided by the bolometric luminosity in each radial bin" (4.4 Deprojected electron temperature and density); "it is computed by integrating the rest-frame X-ray emissivity provided by SPEX over photon energies" (4.4 Deprojected electron temperature and density); "immediately yield the amount of $\sim 3$ keV gas within $r=27$ kpc" (4.5 How much gas is cooling in the Phoenix cluster?)
   - software: SPEX v3.0.5.00
   - parameter: Comparison entropy slopes K ~ r^1.2 (non-radiative) and K ~ r^1.4 (steady-state cooling flow)  
  > "a prediction $K\propto r^{1.4}$ for the steady-state cooling flow (cite: Voit11)" (4.4 Deprojected electron temperature and density)
   - assumption: Mass deposition rate ~2000 Msun/yr (X-ray) and star formation rate 500 Msun/yr used to compute accumulation times  
  > "$\dot{M}_{\rm cool} \sim 2000 ~M_\odot$ yr$^{-1}$ as indicated by the X-ray data (e.g., (cite: McDonald13; Ueda13))" (4.5 How much gas is cooling in the Phoenix cluster?)
   - fitting: _not stated_
   - validation: Entropy profile compared with K ~ r^1.2 and K ~ r^1.4 models  
  > "The observed entropy profile shows a better agreement with $K\propto r^{1.4}$ than $K\propto r^{1.2}$" (4.4 Deprojected electron temperature and density)

## Software

- **CASA** 5.6.1: Imaging of ALMA visibilities  
  > "Imaging was done with the Common Astronomy Software Applications package (CASA: (cite: McMullin07)) version 5.6.1." (Observations and data reduction)
- **tclean** CASA 5.6.1: Multi-Scale CLEAN deconvolution of the SZE image  
  > "using the CASA task *tclean*" (3.2 The Sunyaev-Zel’dovich effect)
- **uvmodelfit** : Fitting compact source positions and flux densities in the uv plane  
  > "we determined their positions and flux densities by fitting with the CASA task *uvmodelfit* the 12-m array visibility data at baselines longer than 30k$\lambda$" (3.1 Compact sources)
- **simobserve** : Producing mock visibilities with thermal noise for imaging simulations  
  > "Visibility data were then produced using the CASA task *simobserve* including both instrumental and atmospheric thermal noise in each spectral window." (4.2 Imaging simulations)
- **CIAO** 4.11 (CALDB 4.8.2): Processing Chandra data  
  > "The data were processed using CIAO version 4.11 (cite: Fruscione06) and the Calibration database (CALDB) version 4.8.2." (4.1 Comparison to X-ray data)
- **XSPEC** 12.10.0e: X-ray spectral fitting and projct deprojection  
  > "Spectral fitting was done with XSPEC version 12.10.0e (cite: Arnaud96)." (4.1 Comparison to X-ray data); "using the model *projct* implemented in XSPEC version 12.10.0e (cite: Arnaud96)" (4.4 Deprojected electron temperature and density)
- **SPEX** v3.0.5.00: X-ray emissivity and bolometric luminosity for deprojection and cooling time  
  > "The X-ray emissivity was computed by SPEX v3.0.5.00 (cite: Kaastra96)" (4.4 Deprojected electron temperature and density)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| SZE decrement significance | >11 | not stated | sigma | 2 | The SZE decrement is detected at more than $11\sigma$ statistical significance. |
| Integrated SZE flux density within theta = 40 arcsec | -11.9 | 0.4 | mJy | 2 | The integrated SZE flux density within $\theta = 40''$ is $-11.9\pm 0.4$ mJy. |
| SZE intensity at SZE peak (5 arcsec smoothed) | -0.294 | 0.025 | mJy/beam | 2 | with the SZE intensities at the two positions of $-0.294 \pm 0.025$ mJy/beam (SZE peak) and $-0.280 \pm 0.025$ mJy/beam (source C1 location) |
| SZE intensity at source C1 location (5 arcsec smoothed) | -0.280 | 0.025 | mJy/beam | 2 | with the SZE intensities at the two positions of $-0.294 \pm 0.025$ mJy/beam (SZE peak) and $-0.280 \pm 0.025$ mJy/beam (source C1 location) |
| Offset of SZE peak from central AGN (C1) | 3.6 arcsec south | not stated | arcsec | 2 | The SZE peak is located at $3.6''$ south from the central AGN (source C1) |
| C1 92 GHz flux density (point-like) | 1.891 | 0.010 | mJy | 1 | $1.891 \pm 0.010$ |
| C2 92 GHz flux density (Gaussian model) | 0.090 | 0.017 | mJy | 1 | $0.090 \pm 0.017$ |
| C3 92 GHz flux density (point-like) | 0.091 | 0.010 | mJy | 1 | $0.091 \pm 0.010$ |
| W 92 GHz flux density (point-like) | 0.158 | 0.010 | mJy | 1 | $0.158 \pm 0.010$ |
| C2 major axis FWHM (elliptical Gaussian) | 1.3 | 0.5 | arcsec | 1 | to obtain the major axis FWHM of $1.3''\pm 0.5''$ and the position angle of $-9.4^\circ \pm 21.8^\circ$ |
| Residual rms after source subtraction (>30 klambda) | 0.0146 | not stated | mJy/beam | 1 | The residuals have the root mean square (rms) value of 0.0146 mJy/beam and are consistent with noise. |
| Missing-flux slope c1 | 0.94 | 0.02 | dimensionless | 4 | This yielded $c_1=0.94 \pm 0.02$ and $c_0= (1.19 \pm 0.16, ~2.07 \pm 0.20, ~3.02 \pm 0.28)$ $\mu$Jy/arcsec$^2$ |
| Offset c0 for ypeak = 4e-4, 8e-4, 12e-4 | 1.19, 2.07, 3.02 | 0.16, 0.20, 0.28 | uJy/arcsec^2 | 4 | This yielded $c_1=0.94 \pm 0.02$ and $c_0= (1.19 \pm 0.16, ~2.07 \pm 0.20, ~3.02 \pm 0.28)$ $\mu$Jy/arcsec$^2$ |
| 1 sigma systematic uncertainty in true intensity from missing-flux offset | 0.24 | not stated | uJy/arcsec^2 | 4 | We regard $\sqrt{2}$ times this value (i.e., $\Delta I_\nu^{\rm in}=0.24 \mu$Jy/arcsec$^2$) |
| Peak incremental Compton y | 5.3e-4 | 0.4 (stat) and 0.3 (sys), in units of 1e-4 | dimensionless | 5 | The peak value is $\Delta y = (5.3 \pm 0.4 \mbox{ [statistical]} \pm 0.3 \mbox{ [systematic]})\times 10^{-4}$ |
| Projected ICM temperature at theta_X < 1.5 arcsec without intrinsic absorption | 9.8 | 1.5 | keV | 3 | the projected ICM temperature at $\theta_{\rm X} < 1.5''$ is $kT=9.8 \pm 1.5$ keV |
| Projected ICM temperature at theta_X < 1.5 arcsec with intrinsic absorption | 2.7 | +0.4/-0.3 | keV | 3 | Inclusion of intrinsic absorption significantly decreases the temperature to $kT=2.7^{+0.4}_{-0.3}$ keV |
| Intrinsic absorber hydrogen column density | 6.7e21 | 1.1e21 | cm^-2 | 3 | the best-fit hydrogen column density of the absorber $N_{\rm H, int}= (6.7 \pm 1.1) \times 10^{21}$ cm$^{-2}$ |
| Intrinsic AGN X-ray luminosity (0.7-7.0 keV) | 1.81e45 h^-2 | 0.09e45 | erg/s | 3 | $L_{\rm X}(0.7-7.0 \mbox{ keV}) = (1.81 \pm 0.09) \times 10^{45} h^{-2}$ erg s$^{-1}$ |
| Upper limit on sqrt(w) = sqrt(dp/drho) within 10 arcsec | <1010 (l/100 kpc)^-1/4 | not stated | km/s | 3 | They lead to an upper limit on $w \equiv \Delta p/\Delta \rho$ of $\sqrt{w} < 1010 (l/100 \mbox{ kpc})^{-1/4}$ km s$^{-1}$. |
| Deprojected temperature at r < 27 kpc (SZE+X-ray, with intrinsic absorption) | 2.70 | 1.71 | keV | 6 | the temperature at $r<27$ kpc is $2.70 \pm 1.71$ keV and $3.01 \pm 1.86$ keV with and without intrinsic absorption, respectively |
| Deprojected temperature at r < 27 kpc (SZE+X-ray, without intrinsic absorption) | 3.01 | 1.86 | keV | 6 | the temperature at $r<27$ kpc is $2.70 \pm 1.71$ keV and $3.01 \pm 1.86$ keV with and without intrinsic absorption, respectively |
| X-ray-only deprojected temperature at r < 20 kpc, with then without intrinsic absorption | 2.73 then 6.37 | +0.24/-0.22 then +0.73/-0.58 | keV | 6 | from $2.73^{+0.24}_{-0.22}$ keV to $6.37^{+0.73}_{-0.58}$ keV once intrinsic absorption is neglected |
| Central temperature relative to mean temperature at r > 300 kpc | ~5 times lower (mean ~16 keV) | not stated | dimensionless | 6 | The inferred central temperature is $\sim 5$ times lower than the mean temperature ($\sim 16$ keV) at $r>300$ kpc. |
| Entropy at r < 27 kpc | <10 | not stated | keV cm^2 | 7 | decreases to $<10$ keV cm$^2$ at $r<27$ kpc |
| Radiative cooling time at r < 27 kpc | ~0.1 | not stated | Gyr | 7 | and drops to $\sim 0.1$ Gyr at $r<27$ kpc |
| Mass of ~3 keV gas within r = 27 kpc | 6.4e11 | 0.9e11 | Msun | 7 | $M_{\rm cool}=(6.4\pm 0.9) \times 10^{11} M_\odot$ |
| Accumulation time of cool gas for Mdot_cool = 2000 Msun/yr | 0.32 | 0.05 | Gyr | 7 | (0.32 \pm 0.05) |
| Time for cool gas to turn into stars for SFR = 500 Msun/yr | 1.3 | 0.2 | Gyr | 7 | (1.3 \pm 0.2) |

## Qualitative findings

- No significant asymmetry or disturbance in the SZE image within current errors; ICM consistent with being isobaric  
  > "We find no significant asymmetry or disturbance in the SZE image within the current measurement errors." (abstract); "This suggests that the ICM in this region is consistent with being isobaric." (4.1 Comparison to X-ray data)
- Inner pressure profile steeper than distant clusters and matches local cool-core clusters  
  > "and is clearly steeper than that from more distant counterparts by (cite: Planck13) and (cite: McDonald14b)" (4.3 Compton y-parameter map and the inner pressure profile)
- Gas density in agreement with Abell 2029 and Abell 1795 at r > 0.2 r500 but systematically higher at smaller radii  
  > "whereas it is systematically higher at smaller radii" (4.4 Deprojected electron temperature and density)
- Entropy profile better matches the steady-state cooling flow slope K ~ r^1.4 than K ~ r^1.2  
  > "The observed entropy profile shows a better agreement with $K\propto r^{1.4}$ than $K\propto r^{1.2}$" (4.4 Deprojected electron temperature and density)

## Claim tuples

- H: Is the Phoenix cluster core disturbed or asymmetric in the SZE? | E: ALMA Band 3 12-m + 7-m SZE image, quadrant radial profiles and residual map after subtracting the mean over an X-ray-defined ellipse | R: SZE detected at >11 sigma; quadrant profiles consistent within errors and no significant disturbance in the residual image | F: No significant asymmetry or disturbance in the SZE image within the current errors | **supported**
- H: Does the inner SZE pressure profile of the Phoenix cluster look like other distant clusters or local cool-core clusters? | E: Compton y map reconstructed from the missing-flux-corrected ALMA image and azimuthal average compared with generalized NFW pressure profiles | R: Profile agrees with Arnaud et al. local cool-core clusters and is steeper than Planck13 and McDonald14b profiles | F: Central concentration is much higher than in other distant clusters and agrees with the local cool-core pressure profile | **supported**
- H: Can SZE plus X-ray imaging measure the central gas temperature while minimising AGN and X-ray absorption contamination? | E: Non-parametric deprojection combining ALMA SZE and Chandra 0.7-2.0 keV images, compared with X-ray-only deprojection with and without intrinsic absorption | R: SZE+X-ray temperature at r < 27 kpc is 2.70 +/- 1.71 keV and 3.01 +/- 1.86 keV with and without absorption, whereas X-ray-only changes from 2.73 to 6.37 keV | F: The method is insensitive to intrinsic absorption | **supported**
- H: Does the gas temperature drop strongly toward the center of the Phoenix cluster? | E: Deprojected temperature profile compared with mean profiles of local and distant cool-core clusters | R: Central temperature ~5 times lower than the ~16 keV at r > 300 kpc; entropy <10 keV cm^2 and cooling time ~0.1 Gyr at r < 27 kpc | F: Gas temperature drops by at least a factor of 5 toward the center, larger than in other clusters, supporting efficient radiative cooling | **supported**
- H: How much gas is cooling efficiently in the Phoenix cluster? | E: Mass of ~3 keV gas within r = 27 kpc from the deprojected profiles | R: Mcool = (6.4 +/- 0.9)e11 Msun, ~20% of the central galaxy stellar mass | F: The gas is cooling efficiently and nearly isobarically down to the inner ~20 h^-1 kpc | **supported**

## Reasoning

- Why this data: X-ray analysis is hampered by a bright AGN and absorbing gas, so an independent SZE probe is needed  
  > "A major challenge in the X-ray analysis of this cluster is the presence of a bright AGN and possibly cold neutral gas in the central galaxy" (Introduction); "It is hence crucial to explore the physical states of the gas by other independent methods." (Introduction)
- Why this method: SZE plus X-ray deprojection is insensitive to X-ray absorbing gas and the central AGN  
  > "Our method can minimize contamination by the central AGN and the X-ray absorbing gas within the cluster, both of which largely affect the X-ray spectrum." (abstract)
- Alternative: C2 as a point source instead of elliptical Gaussian gives a flux about 25% lower; C3 and W also checked with Gaussian models with little change  
  > "For comparison, if source C2 is modeled by a point source, the fitted flux is lower by about 25%" (3.1 Compact sources); "We checked that the results in table [\[tab-source\]](#tab-source) are essentially unchanged when these sources are modeled by a Gaussian varying its full width at half maximum (FWHM) as a free parameter." (3.1 Compact sources)
- Alternative: Intrinsic absorption neglected in X-ray fits gives much higher central temperature  
  > "intrinsic absorption largely modifies the spectral shape at 0.7–2.0 keV and leads to a reduction of the best-fit temperature by more than a factor of 3" (4.1 Comparison to X-ray data)
- How they decided it was enough: _not stated_
- Limitation (authors): Equation-of-state limit is weak  
  > "While the limit is still weak, the observed perturbations in the Phoenix cluster core is consistent with being isobaric" (4.1 Comparison to X-ray data)
- Limitation (authors): Absolute values of the X-ray pseudo pressure are arbitrary  
  > "Note that absolute values of the pseudo pressure are arbitrary" (4.1 Comparison to X-ray data)
- Limitation (authors): Temperature at r > 250 kpc cannot be constrained by the ALMA data  
  > "As the temperature at $r > 250$ kpc ($\theta > 37''$) cannot be constrained by the ALMA data" (4.4 Deprojected electron temperature and density)
- Limitation (authors): X-ray-only deprojection includes statistical errors only  
  > "For simplicity, only statistical errors were taken into account in this particular analysis." (4.4 Deprojected electron temperature and density)
- Caveat (inferred, ours): Deprojected central temperature has a large uncertainty (2.70 +/- 1.71 keV), so the factor-of-5 drop is only weakly constrained by the SZE alone
- Caveat (inferred, ours): Spherical symmetry assumed in the deprojection despite X-ray cavities and N-S asymmetries in the core
- Caveat (inferred, ours): Missing-flux correction rests on simulations that use an X-ray pseudo pressure map as input, with an assumed ypeak normalisation
- Caveat (inferred, ours): Cool gas mass depends on the h = 0.7 choice and adopted mass deposition rates from other papers

## Reproducibility

- Data public (paper): Chandra data from the Chandra Data Archive with ObsIDs listed; ALMA project code given but public status not stated  
  > "The scientific results of this paper are based in part on data obtained from the Chandra Data Archive: ObsID 13401, 16135, 16545, 19581, 19582, 19583, 20630, 20631, 20634, 20635, 20636, and 2079." (Acknowledgements); "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00894.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: tclean image size, cell size and iteration limits
- Missing: Target field centre coordinates (blank in the text)
- Missing: Deprojection code and fitting algorithm details
- Missing: Initial values and fixed AGN parameters of the Chandra spectral model
- Missing: Compact source positions (blank in the table)
- Data volume (inferred): ALMA: roughly tens of GB of raw/calibrated measurement sets (12-m 3.2 hr plus 7-m 8.1 hr, 7-pointing mosaic, 4 continuum windows); Chandra: 12 ACIS-I ObsIDs, a few GB
- Score (inferred): 3/5, Observation setup, tclean multi-scale parameters, uvmodelfit usage and key numeric results are given, but image/cell size, iteration limits, mosaic phase centre, deprojection algorithm details and Chandra reprocessing choices are missing, and no code is released.
- Rediscovery candidate: yes, The ALMA project code is given and Chandra ObsIDs are listed; the SZE imaging recipe (scales, mask, threshold, gain, weighting) and numeric results (flux density -11.9 mJy, 11 sigma, c1 = 0.94) are specific enough to redo, although the deprojection part is only partially specified.

## Links

- Method: (cite: Kitayama16) (Earlier ALMA SZE imaging procedure, error equation, simulation relation and 6% calibration uncertainty)
- Method: (cite: Steeb19) (Modified Multi-Scale CLEAN in CASA 5.6.0)
- Method: (cite: Ueda18) (Equation-of-state analysis of perturbations)
- Method: (cite: Sanders06) (Contour binning algorithm used for X-ray mapping)
- Method: (cite: McDonald19) (Chandra spectral treatment with intrinsic absorption)
- Companion: (cite: Akahori19) (ATCA 18 GHz properties of the same compact sources)
- Companion: (cite: McDonald15) (Chandra X-ray pressure profile and cavities in the Phoenix cluster)
- Related: South Pole Telescope (SPT) cluster survey
- Related: Chandra ACIS-I observations of the Phoenix cluster

## Checks

```json
{
 "quotes": 178,
 "quotes_ok": 178,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 29,
 "numeric_problems": 0,
 "fill": {
  "facts": 129,
  "stated": 111,
  "rate": 0.86
 },
 "evidence_ok": true
}
```
