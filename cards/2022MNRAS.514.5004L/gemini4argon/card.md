# Candidate high-redshift protoclusters and lensed galaxies in the Planck list of high-z sources overlapping with Herschel-SPIRE imaging

`2022MNRAS.514.5004L` | Monthly Notices of the Royal Astronomical Society 2022 | first author: Lammers, Caleb | arXiv: 2204.06752 | DOI: 10.1093/mnras/stac1555

Card schema 1.0 | model gemini-4-argon | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies, galaxy_clusters_and_sz, cosmology
- Question: What is the true statistical nature of the Planck list of high-z source candidates (PHz catalogue) in an unbiased sample of 187 sources observed with Herschel-SPIRE, and how many candidate protoclusters and strong gravitational lenses does it contain?  
  > "To this end, we have used archival *Herschel*-SPIRE observations to study a uniformly-selected sample of 187 PHz sources." (Abstract); "In order to correctly deduce the nature of the PHz catalogue, in this paper we investigate a sample of 187 unbiased *Herschel*-SPIRE observations of PHz sources that serendipitously fall within the 1270 deg$^{2}$ coverage of the *Herschel* wide-field surveys" (Introduction)
- Target **PLCK_G224.6-40.7**: coordinates 04:33:19.24 -25:46:32.22  
  > "| $^{a}$PLCK_G224.6$-$40.7 | 04:33:19.24 | $-$25:46:32.22 | 154 $\pm$ 6 | 215 $\pm$ 5 | 199 $\pm$ 6 | 1.00 |" (Candidate lensed galaxies in the PlanckXXVII sources); "One of the best lensed candidates from the PlanckXXVII sources, G224, has recently been followed up with ALMA and confirmed as a new *Planck*-identified strong gravitationally-lensed galaxy (Fig. [16](#G224ALMA))." (New candidate lensed galaxies); z/distance _not stated_; distance from _not stated_
- Target **187 PHz HELP sources**: coordinates _not stated_; z/distance z ~ 2  
  > "Hereafter, these 187 PHz sources that lie in the HELP fields will be referred to as the ‘PHz HELP sources’." (The Herschel Extragalactic Legacy Project); "In agreement with PlanckXXVII, we find that the redshift distribution of galaxies in the PHz HELP sources peaks at $z\,{\approx}\,2$." (Photometric redshifts and star-formation rates); distance from Photometric redshift from modified blackbody fit to Herschel-SPIRE bands  
  > "Hereafter, these 187 PHz sources that lie in the HELP fields will be referred to as the ‘PHz HELP sources’." (The Herschel Extragalactic Legacy Project); "In agreement with PlanckXXVII, we find that the redshift distribution of galaxies in the PHz HELP sources peaks at $z\,{\approx}\,2$." (Photometric redshifts and star-formation rates)
- Target **228 PlanckXXVII sources**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2019.1.01155.S
- bands: _not stated_
- frequencies and spectral setup: 870 um continuum  
  > "The 870-$\mu$m ALMA image has spatially resolved G224, revealing a clear Einstein ring." (New candidate lensed galaxies)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **Herschel-SPIRE / HELP**: Homogeneous archival 250, 350, and 500 um wide-field survey images covering 1270 deg^2 from HELP DR1, plus dedicated follow-up maps of 228 PlanckXXVII sources from the ESA Herschel Science Archive.  
  > "In particular, HELP DR1 provides homogeneous SPIRE 250-, 350- and 500-$\mu$m images for each of the HELP fields." (The Herschel Extragalactic Legacy Project); "The PlanckXXVII SPIRE maps are available through the ESA Herschel Science Archive (<http://archives.esac.esa.int/hsa/whsa>)." (Data availability)
- Other facility **Planck**: All-sky maps at 217, 353, 545, and 857 GHz and the PHz catalogue of 2151 high-redshift source candidates.  
  > "*Planck* mapped the whole sky between 30 and 857 GHz, including channels centred at 217, 353 and 545 GHz (cite: PlanckI2013)." (The Planck List of High-z Source Candidates); "The resulting catalogue consists of 2151 potential high-$z$ sources, spread across the northern and southern Galactic hemispheres (see Fig. [1](#HELP-fields))." (The Planck List of High-z Source Candidates)
- External data: PHz catalogue of 2151 high-z source candidates  
  > "In addition to the various compact source catalogues, the Planck Collaboration released a catalogue of 2151 potential high-$z$ sources (the Planck list of high-$z$ source candidates, or PHz) by looking at peaks in the cosmic infrared background (cite: PlanckPHz2016)." (Introduction) [from (cite: PlanckPHz2016)]
- External data: PlanckXXVII sample of 228 Planck-selected high-z candidates observed with Herschel-SPIRE  
  > "(cite: PlanckHerschel2015), hereafter PlanckXXVII, performed a dedicated *Herschel*-SPIRE follow up of 228 *Planck*-selected high-$z$ candidates, consisting of red sources from the PCCS and sources selected in a similar manner to the PHz catalogue." (Introduction) [from (cite: PlanckHerschel2015)]
- External data: HELP DR1 250, 350, and 500 um images over 1270 deg^2  
  > "HELP combines the *Herschel*-SPIRE survey fields into a consistent single data release spanning a total of 1270 deg$^{2}$ on the sky (cite: HELP2021)." (The Herschel Extragalactic Legacy Project) [from (cite: shirley2021); (cite: HELP2021)]
- External data: Confirmed high-z strong gravitationally-lensed galaxies and SCUBA-2 protocluster candidates used to build the ML training set  
  > "Specifically, we include the two highest redshift lensed galaxies from (cite: NegrelloLenses2010), namely SDP.81 at $z\,{=}\,3.04$ (cite: ALMASDP812015) and SDP.130 at $z\,{=}\,2.63$, as well as all of the lensed galaxies from (cite: WeissLensed2013) that have a peak flux density ${>}\,$100 mJy at 350 or 500 $\mu$m (16 galaxies total)." (Training and test sets); "(cite: MacKenzieSCUBA2017) and (cite: ChengSCUBA2020) followed up large samples of PHz sources with SCUBA-2 at 850 $\mu$m and selected 45 sources as protocluster candidates, based on their overdensities at this wavelength." (Training and test sets) [from (cite: CanamerasPlanckGEMS2015); (cite: FuLensed2012); (cite: CombesLensed2012); (cite: NegrelloLenses2010); (cite: WeissLensed2013); (cite: MacKenzieSCUBA2017); (cite: ChengSCUBA2020)]
- External data: Stacked radial surface brightness profiles of 53 z ~ 1 near-IR-selected galaxy clusters observed by Herschel-SPIRE  
  > "Currently, statistical samples of protoclusters at higher redshift do not exist, but at $z\,{\approx}\,1$ (cite: Albertsclusters2020) studied 53 near-IR-selected galaxy clusters observed by *Herschel*-SPIRE at 250, 350 and 500 $\mu$m." (The spatial distribution of star-formation in z ~ 2 protoclusters) [from (cite: Albertsclusters2020)]
- Simulation/model as data: Simulated Infrared Dusty Extragalactic Sky (SIDES) 2 deg^2 simulation at 250, 350, 500, and 850 um  
  > "Specifically, we repeated the PHz selection algorithm on the Simulated Infrared Dusty Extragalactic Sky (cite: BetherminSIDES2017) simulation data." (The nature of the PHz sources)
- Simulation/model as data: Monte Carlo mock sky over 5000 deg^2 using the analytic 545 GHz clump luminosity function model of Negrello et al. (2017)  
  > "Specifically, we employ the analytic model developed by (cite: Negrello2017), which gives the luminosity function (LF) of clumps (either an isolated galaxy or a physically bound group of galaxies) at 545 GHz based on galaxy evolution models and the infrared LFs of individual galaxies" (The nature of the PHz sources); "Following the simple Monte Carlo simulations done by (cite: Negrello2017), we draw clumps from the LF of their model, and distribute them randomly over 5,000 deg$^2$ of a mock sky" (The nature of the PHz sources)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Definition of IN region as the contour enclosing 50 per cent of the Planck 545 GHz peak flux density, noise estimation via Gaussian fit to map pixel histograms, 350-um-centred band matching, Lockman-SWIRE random field comparison, overdensity contrast definition, and dust emissivity index beta = 1.5  
  > "In order to study the number counts of SPIRE-detected galaxies in the PHz catalogue, we define an ‘IN region’ in the same way as in PlanckXXVII." (SPIRE-detected galaxies within PHz sources); "Before performing photometry, we measure the noise at each wavelength across all of the HELP fields in a similar fashion to PlanckXXVII (Table [\[HELP-table\]](#HELP-table))." (Independent photometry); "$\beta$ is the dust emissivity index, which is fixed to 1.5 (the same value adopted in PlanckXXVII)" (Photometric redshifts and star-formation rates) [from PlanckXXVII (cite: PlanckHerschel2015)]
- Simplified Poisson probability calculation for photometric redshift clustering in redshift bins  
  > "To do so, we follow a simplified version of an algorithm detailed by (cite: Castignani2014), which utilizes a background photometric redshift distribution to calculate Poisson probabilities within redshift bins." (Photometric redshift clustering in 3 sigma spatial overdensities) [from (cite: Castignani2014)]
- Monte Carlo simulation of 545 GHz clumps to test line-of-sight alignments  
  > "Following the simple Monte Carlo simulations done by (cite: Negrello2017), we draw clumps from the LF of their model, and distribute them randomly over 5,000 deg$^2$ of a mock sky" (The nature of the PHz sources) [from (cite: Negrello2017)]
- Radial profile bin sizes and normalization to 0.5 at 27.5 arcsec for cluster stack comparison  
  > "Here we have followed (cite: Albertsclusters2020), adopting the same bin sizes and arbitrarily normalizing the profiles to a value of 0.5 at 27.5 arcsec." (The spatial distribution of star-formation in z ~ 2 protoclusters) [from (cite: Albertsclusters2020)]

### Not stated but needed to reproduce (our reading)

- All ALMA observation, calibration, and imaging parameters for PLCK_G224.6-40.7 (project 2019.1.01155.S), including array configuration, angular resolution, sensitivity, and CASA version
- Which 9 of the 228 PlanckXXVII sources could not be recovered from the Herschel Science Archive
- Exact list of the 45 SCUBA-2 protocluster candidate fields used to extract the 388 unlensed training galaxies

## Analysis recipe

1. **Define PHz source IN regions and perform Herschel-SPIRE 250, 350, and 500 um photometry and band-merging**: Smooth Planck 545 GHz map with a 2.0 arcmin FWHM Gaussian to find the 50% peak flux contour (or use a 4.34 arcmin radius circle if open); measure map noise via Gaussian fits to pixel histograms; detect peaks above 4*sigma_bar in PSF-convolved SPIRE maps, fit fixed-FWHM Gaussian PSFs (simultaneously if within 2*FWHM), and band-merge anchored on 350 um detections.  
  > "We determine the IN region contour by smoothing the 545-GHz map with a 2.0 arcmin full width at half-maximum (FWHM) Gaussian, then find the contour on the smoothed 545-GHz map corresponding to 50 per cent of the peak flux density of the source." (SPIRE-detected galaxies within PHz sources); "Photometry is performed on sky-subtracted mean-0 maps using Gaussian point-spread functions (PSFs) with FWHMs of 18.15, 25.15 and 36.30 arcsec for the 250-, 350- and 500-$\mu$m maps, respectively (cite: Griffin2010)." (Independent photometry); "Matching galaxies detected across the 250-, 350- and 500-$\mu$m maps is done by focusing on the galaxies detected at 350 $\mu$m (also see PlanckXXVII)." (Galaxy matching)
   - parameter: Detection thresholds of 32.0, 34.6, and 38.5 mJy (4*sigma_bar) at 250, 350, and 500 um; Gaussian PSF FWHMs of 18.15, 25.15, and 36.30 arcsec  
  > "The cutoff flux densities are 32.0, 34.6 and 38.5 mJy at 250, 350 and 500 $\mu$m, respectively." (Independent photometry); "Photometry is performed on sky-subtracted mean-0 maps using Gaussian point-spread functions (PSFs) with FWHMs of 18.15, 25.15 and 36.30 arcsec for the 250-, 350- and 500-$\mu$m maps, respectively (cite: Griffin2010)." (Independent photometry)
   - assumption: SPIRE beams are well-approximated by circular Gaussians with fixed FWHMs.  
  > "A Gaussian PSF fit is then performed on each detected galaxy in the non-convolved map, with a fixed FWHM (depending on the wavelength), and initial position/amplitude guesses from the convolved map." (Independent photometry)
   - fitting: Gaussian PSF fitting in non-convolved maps with free amplitude and position constrained within 0.5*FWHM, using simultaneous PSF fitting when galaxies lie within 2*FWHM.  
  > "During PSF fitting, the PSF amplitude is allowed total freedom, but the positions are allowed to shift only slightly from the initial position ($0.5\,{\times}\,$FWHM in each direction) to avoid accidentally fitting the PSF to a separate nearby galaxy instead of the intended galaxy." (Independent photometry); "Whenever multiple galaxies are detected within two FWHMs of each other (corresponding to 6.0, 5.1 and 5.2 pixels at 250, 350 and 500 $\mu$m, respectively), galaxy flux densities and positions are measured with simultaneous PSF fitting." (Independent photometry)
   - validation: Compared galaxy detection and photometry against other comparable codes such as SUSSEXtractor.  
  > "We find that our galaxy detection and photometry values are largely consistent with the results from other comparable codes, including codes developed specifically for *Herschel*-SPIRE observations (e.g., sussextractor; (cite: PearsonHIPE2014))." (Independent photometry)
2. **Compute source statistics, photometric redshifts, SFRs, and stacked surface brightness profiles**: Compare Planck flux distributions, Euclidean-normalized number counts, galaxy surface densities, overdensity contrasts, and SPIRE colours against PlanckXXVII and 10,000 random 4.34-arcmin apertures in Lockman-SWIRE using two-sample KS tests; fit modified blackbody SEDs for photo-z, L_FIR, and SFR; stack 250, 350, and 500 um cutouts centred on the brightest 350 um galaxy.  
  > "To compare the number counts of IN region galaxies with the number counts of random locations, we compute the number counts at 10,000 random positions in Lockman-SWIRE within a circle of radius 4.34 arcmin (the median size of the IN regions)." (Number counts); "For each galaxy in our sample, we fit the three SPIRE flux densities to a modified blackbody SED of the form" (Photometric redshifts and star-formation rates); "We create mean image stacks by averaging the 250-, 350- and 500-$\mu$m maps centred on the position of the brightest 350-$\mu$m galaxy in each IN region." (Source stacking and surface brightness profiles)
   - parameter: Red colour cuts S350/S250 = 1.2 and S500/S350 = 0.8; background subtraction beyond 9 arcmin for stacks  
  > "Based on the distribution of random galaxy colours, we set the thresholds $S_{350}/S_{250}\,{=}\,1.2$ and $S_{500}/S_{350}\,{=}\,0.8$ to select the reddest galaxies, falling in the upper-right region of Fig. [8](#colourscatter)." (Colours); "Before computing the average, we set the background of each image to 0 Jy beam$^{-1}$ by subtracting the mean intensity value in pixels that are ${>}\,9$ arcmin from the centre." (Source stacking and surface brightness profiles)
   - assumption: Standard LambdaCDM cosmology from Planck Collaboration 2018; single dust temperature T = 30 K, dust emissivity index beta = 1.5, nu_0 = 3000 GHz, sub-dominant AGN, and Chabrier IMF conversion factor 0.95e-10 Msun yr^-1 Lsun^-1.  
  > "Throughout this paper, we assume a standard $\Lambda$CDM cosmology with parameters from (cite: PlanckParams2018)." (Introduction); "$\beta$ is the dust emissivity index, which is fixed to 1.5 (the same value adopted in PlanckXXVII) and $T$ is the dust temperature. In order to make progress, we set $T\,{=}\,30\,$K for all of the galaxies in the analysis." (Photometric redshifts and star-formation rates); "Next, we calculate far-IR luminosities ($L_{\rm FIR}$) by integrating our fits to Eq. [\[mbb\]](#mbb) between 8 and 1000 $\mu$m (in the rest-frame), and convert these to SFRs using a conversion factor of $0.95\,{\times}\,10^{-10}\,{\rm M}_{\odot}\,{\rm yr}^{-1}\,{\rm L}_{\odot}^{-1}$, which assumes a Chabrier initial mass function (cite: chabrier2003)." (Photometric redshifts and star-formation rates)
   - fitting: Modified blackbody fit to 250, 350, and 500 um flux densities.  
  > "For each galaxy in our sample, we fit the three SPIRE flux densities to a modified blackbody SED of the form" (Photometric redshifts and star-formation rates)
   - validation: Tested sensitivity to dust temperature by repeating fits with T = 25 K and T = 35 K, and tested alternative stacking on flux-weighted centroids.  
  > "We find similar trends when instead adopting a dust temperature of $T\,{=}\,25\,$K or $T\,{=}\,35\,$K, and use the change in the median of the redshift distribution to make an estimate of the redshift uncertainty of $\delta z \approx 1$." (Photometric redshifts and star-formation rates); "We explored other stacking choices as well, including stacking on the flux-weighted centroid positions, and found similar trends." (Footnote 2)
3. **Select >3 sigma protocluster candidates, evaluate redshift clustering, and test line-of-sight alignments with simulations**: Derive 3 sigma galaxy surface density thresholds from 10,000 random Lockman-SWIRE regions; select PHz sources exceeding the 3 sigma threshold in at least one SPIRE band with >5 galaxies at 350 um; compute Poisson redshift clustering probabilities in bins of width Delta z = 1; run PHz/overdensity selection on SIDES and 5000 deg^2 Negrello et al. (2017) Monte Carlo clump simulations.  
  > "With these thresholds, we identify the most promising potential protoclusters as those that are ${>}\,3\,\sigma$ overdense at 250, 350 or 500 $\mu$m (see Table [\[protoclustertable\]](#protoclustertable))." (3 sigma spatial overdensities); "Thus, for each redshift bin in each of the 40 protocluster candidate sources, we calculate $P_{\rm clust}$ using Eq. [\[clustering_eq\]](#clustering_eq) with $\Delta z\,{=}\,1$, and show the results in Fig. [15](#zclustering) (faint grey lines)." (Photometric redshift clustering in 3 sigma spatial overdensities); "Following the simple Monte Carlo simulations done by (cite: Negrello2017), we draw clumps from the LF of their model, and distribute them randomly over 5,000 deg$^2$ of a mock sky" (The nature of the PHz sources)
   - parameter: 3 sigma surface density thresholds of 1220, 970, and 430 deg^-2 at 250, 350, and 500 um; >5 galaxies at 350 um; Delta z = 1 smoothed with a Gaussian kernel of width 0.1  
  > "A random source made up of 20 galaxies has a surface density of $1220$ deg$^{-2}$, providing an approximate 3$\,\sigma$ galaxy surface density threshold. Likewise, at 350 $\mu$m, 3$\,\sigma$ random sources of $S_{350}\,{>}\,34.6\,$mJy galaxies contain 16 galaxies, corresponding to a 3$\,\sigma$ surface density of $970$ deg$^{-2}$. Lastly, the 3$\,\sigma$ surface density of $S_{500}\,{>}\,38.5\,$mJy galaxies is $430$ deg$^{-2}$." (3 sigma spatial overdensities); "To exclude these artificially-overdense sources from the list of candidate protoclusters, we adopt a conservative, arbitrary threshold of ${>}\,$5 galaxies at 350 $\mu$m, which results in a total of 40 ${>}\,3\,\sigma$ protocluster candidates" (3 sigma spatial overdensities); "Note that the results here have been smoothed by a Gaussian kernel with a width of 0.1, which is much smaller than the photometric redshift uncertainty, and therefore should not introduce any biases." (Photometric redshift clustering in 3 sigma spatial overdensities)
   - fitting: _not stated_
   - validation: Compared 3 sigma total-density selection with 3 sigma red-galaxy density selection (finding 71% overlap).  
  > "In addition to these criteria identifying a similar number of candidate protoclusters, there is significant overlap between the 40 candidates from above and the 38 red candidates; 27 of the 38 red candidates (71 per cent) are included among the 40 overdense locations, supporting the potential high-$z$ nature of the protocluster candidates." (3 sigma spatial overdensities)
4. **Identify candidate strong gravitationally-lensed galaxies using an ensemble neural network and linear flux thresholds, and confirm PLCK_G224.6-40.7 with ALMA**: Train an ensemble of 100 single-layer neural networks on 250, 350, and 500 um galaxy flux densities using 31 known high-z lensed galaxies and 388 unlensed protocluster galaxies; classify galaxies with average ML score >= 0.5 as lens candidates; optimize linear demarcation lines in flux space by maximizing the F1 score; confirm candidate PLCK_G224.6-40.7 via 870 um ALMA imaging.  
  > "Our final ML classification model consists of 100 ensemble NNs. Each NN has three input nodes (corresponding to galaxy flux densities at 250, 350 and 500 $\mu$m), one hidden layer of 20 nodes, and a single output node, for which an output of 1.0 corresponds to a lensed galaxy and 0.0 corresponds to an un-lensed star-forming galaxy." (Neural-network model); "In other words, for each of the plots in Fig. [18](#manuallearningscatter), we search the two-dimensional parameter space to find the slope and intercept of the line that maximizes the $F_1$ score with respect to the ML model’s classifications." (New threshold selection criteria); "The 870-$\mu$m ALMA image has spatially resolved G224, revealing a clear Einstein ring." (New candidate lensed galaxies)
   - software: PyTorch
   - parameter: 100 NNs, 3 input nodes, 1 hidden layer of 20 nodes (ReLU), 1 output node (sigmoid), ADAM optimizer, 5000 epochs, learning rate 0.01, classification threshold 0.5  
  > "Each NN has three input nodes (corresponding to galaxy flux densities at 250, 350 and 500 $\mu$m), one hidden layer of 20 nodes, and a single output node, for which an output of 1.0 corresponds to a lensed galaxy and 0.0 corresponds to an un-lensed star-forming galaxy." (Neural-network model); "We simultaneously train all 100 NNs over 5000 epochs (using the full training set every epoch) with a learning rate of 0.01, and average their outputs to obtain a final ML score. We use a standard, albeit arbitrary, cutoff at 0.5 to identify new lensed galaxies." (Neural-network model)
   - assumption: Galaxies with S350 or S500 <= 100 mJy in the 45 SCUBA-2 protocluster candidate fields are unlensed star-forming galaxies.  
  > "Again, motivated by the criteria used to select gravitationally-lensed galaxies, we do not include galaxies with flux densities ${>}\,100\,$mJy at 350/500 $\mu$m in the unlensed training set (11 galaxies across the 45 sources)." (Training and test sets)
   - fitting: Supervised neural network training with ADAM optimizer and grid optimization of linear threshold slope/intercept to maximize F1 score.  
  > "We adopt a standard rectified linear unit (ReLU; (cite: NairReLU2010)) activation function for the hidden layer, a sigmoid (or logistic) activation function for the output layer, and the adaptive moment estimation optimizer (ADAM; (cite: KingmaADAM2014))." (Neural-network model); "To incorporate both the accuracy and precision of the demarcation line criteria in searching for the best line, we optimize for the line’s $F_1$ score (the harmonic mean of the precision and recall: $F_1 = 2/(\mathrm{recall}^{-1} + \mathrm{precision}^{-1})$)." (New threshold selection criteria)
   - validation: Evaluated on a 20% held-out test set (84 galaxies, ~100% accuracy), compared against the S500 > 100 mJy cut and known lensed galaxy SEDs, and confirmed G224 with ALMA 870 um imaging.  
  > "For model validation, we randomly select 20 per cent of the training set (84 galaxies) to be a test set, on which the model is tested but not trained." (Training and test sets); "We find that a simple NN model consistently trains to about 100 per cent accuracy on the test set" (Neural-network model); "One of the best lensed candidates from the PlanckXXVII sources, G224, has recently been followed up with ALMA and confirmed as a new *Planck*-identified strong gravitationally-lensed galaxy (Fig. [16](#G224ALMA))." (New candidate lensed galaxies)

## Software

- **PyTorch** : Constructing and training the ensemble neural network model to classify candidate gravitationally-lensed galaxies.  
  > "We construct our ML model using PyTorch (cite: Paszke2019)." (Neural-network model)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Fraction of bright (peak flux >= 300 mJy) gravitationally-lensed galaxies in PHz HELP sample | 0.5 | not stated | per cent | 4 | Notice that in the PHz HELP sources, we find only one exceptionally bright (peak flux density ${\gtrsim}\,300$ mJy) strong gravitationally-lensed galaxy out of 187 sources (0.5 per cent) |
| Number of >3 sigma protocluster candidates in PHz HELP sample | 40 | not stated | dimensionless | 3 | In total, these 40 promising protocluster candidates make up 21 per cent of the total PHz HELP sample, including nine sources that are ${>}\,3\,\sigma$ overdense at 250 $\mu$m (4.8 per cent), 26 at 350 $\mu$m (14 per cent) and 36 at 500 $\mu$m (19 per cent). |
| Sky density of >3 sigma overdense protocluster candidates in PHz catalogue | 3.1e-2 | not stated | deg^-2 | 3 | However, because the PCCS contains significantly more sources than the PHz catalogue, the density on the sky of ${>}\,3\,\sigma$ overdense protocluster candidates in the PCCS catalogue ($3.3\,{\times}\,10^{-2}$ deg$^{-2}$) is comparable to the density in the PHz catalogue ($3.1\,{\times}\,10^{-2}$ deg$^{-2}$). |
| Peak of photometric redshift distribution of PHz HELP galaxies | 2 | 1 | dimensionless | 2 | We find similar trends when instead adopting a dust temperature of $T\,{=}\,25\,$K or $T\,{=}\,35\,$K, and use the change in the median of the redshift distribution to make an estimate of the redshift uncertainty of $\delta z \approx 1$.; In agreement with PlanckXXVII, we find that the redshift distribution of galaxies in the PHz HELP sources peaks at $z\,{\approx}\,2$. |
| Fraction of PHz HELP galaxies peaking at 350 um | 66 | not stated | per cent | 2 | Instead, most PHz HELP galaxies (66 per cent) peak at 350 $\mu$m, whereas only 41 per cent of galaxies in the PlanckXXVII sources peak at 350 $\mu$m. |
| Number of new ML-selected candidate lensed galaxies in PHz HELP sample | 7 | not stated | dimensionless | 4 | Our machine-learning approach identified a total of seven new candidate lensed galaxies among the PHz HELP sources whose SEDs are consistent with being high-$z$ gravitational lenses. |
| Number of new ML-selected candidate lensed galaxies in PlanckXXVII sample | 13 | not stated | dimensionless | 4 | Applying our ML model to galaxies within the PlanckXXVII sources, we find that we can identify 13 new candidate lensed galaxies from the PlanckXXVII sources (see Table [\[PlanckXXVIIlensedtable\]](#PlanckXXVIIlensedtable)). |
| Herschel-SPIRE 250 um flux density of ALMA-confirmed lens PLCK_G224.6-40.7 | 154 | 6 | mJy | 1 | / $^{a}$PLCK_G224.6$-$40.7 / 04:33:19.24 / $-$25:46:32.22 / 154 $\pm$ 6 / 215 $\pm$ 5 / 199 $\pm$ 6 / 1.00 / |
| Herschel-SPIRE 350 um flux density of ALMA-confirmed lens PLCK_G224.6-40.7 | 215 | 5 | mJy | 1 | / $^{a}$PLCK_G224.6$-$40.7 / 04:33:19.24 / $-$25:46:32.22 / 154 $\pm$ 6 / 215 $\pm$ 5 / 199 $\pm$ 6 / 1.00 / |
| Herschel-SPIRE 500 um flux density of ALMA-confirmed lens PLCK_G224.6-40.7 | 199 | 6 | mJy | 1 | / $^{a}$PLCK_G224.6$-$40.7 / 04:33:19.24 / $-$25:46:32.22 / 154 $\pm$ 6 / 215 $\pm$ 5 / 199 $\pm$ 6 / 1.00 / |
| Fraction of simulated protocluster candidates containing 2 or more unconnected line-of-sight clumps | 96 | not stated | per cent | 3 | Upon investigating these simulated protocluster candidates, we find that 96 per cent of them contain two or more clumps aligned along the line-of-sight that are not physically connected to one another. |
| Average flux density ratio between brightest and second brightest clump along simulated PHz lines of sight | 4.4 | not stated | dimensionless | 3 | The average flux density ratio between the brightest and second brightest clumps is about 4.4, in comparison with 1.5 for random directions. |

## Qualitative findings

- The 187 PHz HELP sources are statistically representative of the full 2151-source PHz catalogue, whereas the 228 PlanckXXVII sources were significantly biased towards brighter, more compact sources.  
  > "In other words, the 187 PHz HELP sources are drawn from the same distribution as the entire PHz sample, and are therefore representative of the overall PHz catalogue." (Planck flux densities)
- Average PHz HELP sources are less bright in stacked SPIRE emission than PlanckXXVII sources, but show clustering extending to ~5 arcmin, are more centrally concentrated than PlanckXXVII sources, and are physically more extended in the far-IR than z ~ 1 near-IR-selected galaxy clusters.  
  > "We thus conclude that the PHz HELP sources are less bright, but more centrally-concentrated than the PlanckXXVII sources." (Source stacking and surface brightness profiles); "Interestingly, we find that the average far-infrared extent of the PHz HELP sources is much larger than that of the average $z\,{\approx}\,1$ cluster" (The spatial distribution of star-formation in z ~ 2 protoclusters)
- ALMA 870 um imaging spatially resolves candidate PLCK_G224.6-40.7 into an Einstein ring, confirming that fainter (peak flux ~100-200 mJy) gravitationally-lensed galaxies exist within overdense Planck-selected fields.  
  > "The 870-$\mu$m ALMA image has spatially resolved G224, revealing a clear Einstein ring. This supports the suspected presence of gravitationally-lensed galaxies among the PHz sources that are less extreme than the *Planck* GEMS." (New candidate lensed galaxies)

## Claim tuples

- H: The previously reported ~5% fraction of ultra-bright (peak flux >= 300 mJy) strong gravitationally-lensed galaxies in PlanckXXVII is representative of the full PHz catalogue. | E: Search an unbiased sample of 187 PHz sources in the Herschel-SPIRE HELP fields for bright gravitationally-lensed galaxies. | R: Only 1 out of 187 PHz HELP sources (0.5%, G160) is a bright (peak flux >= 300 mJy) strong gravitationally-lensed galaxy, compared to 12/228 (5%) in PlanckXXVII. | F: Ultra-bright gravitationally-lensed galaxies are rarer in the PHz catalogue (<1%) than previously believed by about an order of magnitude. | **refuted**
- H: Typical PHz sources in an unbiased sample consist of spatial overdensities of red, star-forming galaxies at z ~ 2-3 (candidate protoclusters). | E: Measure SPIRE galaxy number counts, overdensity contrasts, colours, modified-blackbody photometric redshifts, and image stacks for 187 PHz HELP sources compared to 10,000 random Lockman-SWIRE fields. | R: PHz HELP galaxy densities reject the random distribution at >8 sigma across all three bands, 40/187 sources (21%) are >3 sigma overdense, stacked emission extends to ~5 arcmin, and photometric redshift clustering peaks at z = 2-3. | F: The vast majority of PHz sources are spatial overdensities of red galaxies at z ~ 2-3, with a >3 sigma protocluster candidate fraction (21%) comparable to that of the biased PlanckXXVII sample (25%). | **supported**
- H: Less extreme (peak flux ~ 100-200 mJy) strong gravitationally-lensed galaxies exist within PHz sources, including within galaxy overdensities, and can be identified via machine learning on SPIRE fluxes. | E: Train a 100-network ensemble neural network on 250, 350, and 500 um flux densities to classify individual SPIRE galaxies in PHz HELP and PlanckXXVII fields, and follow up candidate PLCK_G224.6-40.7 with ALMA at 870 um. | R: The ML classifier identifies 7 new candidate lensed galaxies in the PHz HELP sample and 13 in the PlanckXXVII sample; ALMA 870 um observations resolve PLCK_G224.6-40.7 into an Einstein ring. | F: Less extreme strong gravitationally-lensed galaxies are present in PHz overdensities and can be selected using either the ensemble NN or two linear flux-threshold demarcation lines. | **supported**
- H: Projected galaxy overdensities in PHz protocluster candidates are single physically-bound structures at one redshift rather than chance line-of-sight alignments. | E: Run the PHz and >3 sigma overdensity selection on a 5000 deg^2 Monte Carlo mock sky generated from the Negrello et al. (2017) 545 GHz clump luminosity function. | R: 96% of simulated protocluster candidates contain 2 or more unconnected clumps along the line of sight (mean of ~4 clumps), but the brightest clump is on average 4.4 times brighter than the second brightest clump. | F: PHz protocluster candidates typically suffer from line-of-sight interlopers, but are usually dominated by a single bright clump at one redshift. | **partially**

## Reasoning

- Why this data: The 1270 deg^2 HELP DR1 homogenized Herschel-SPIRE survey fields serendipitously overlap with 187 PHz sources, providing a large, uniform, unbiased sample to overcome the selection biases of PlanckXXVII.  
  > "In order to correctly deduce the nature of the PHz catalogue, in this paper we investigate a sample of 187 unbiased *Herschel*-SPIRE observations of PHz sources that serendipitously fall within the 1270 deg$^{2}$ coverage of the *Herschel* wide-field surveys, now combined into a single data release by the *Herschel* Extragalactic Legacy Project (cite: shirley2021)." (Introduction)
- Why this method: Planck 545 GHz 50% peak contours enclose extended PHz sources better than fixed circles; random Lockman-SWIRE apertures avoid kernel density estimator false positives; and an ensemble of 100 NNs trained on individual galaxy fluxes avoids CNN small-sample/resolution issues and stabilizes random weight initialization.  
  > "We find that using a contour on the *Planck* 545-GHz map generally encloses sources more effectively than a circular IN region." (SPIRE-detected galaxies within PHz sources); "To obtain more easily-interpretable significance estimates, we instead turn to a comparison with the distributions of galaxy densities from random positions in the Lockman-SWIRE field, which allow us to estimate 3$\,\sigma$ overdensity thresholds" (3 sigma spatial overdensities); "We adopt an ensemble learning technique in which we simultaneously train many NN models and use the average of their outputs for more consistent classification (cite: HansenNN1990)." (Neural-network model)
- Alternative: Circular IN regions centred on the Planck position (rejected as primary definition because 545 GHz 50% flux contours better enclose extended sources, though used as fallback and for 1-arcmin flux ratio tests).  
  > "We find that using a contour on the *Planck* 545-GHz map generally encloses sources more effectively than a circular IN region." (SPIRE-detected galaxies within PHz sources)
- Alternative: Kernel density estimator (KDE) techniques for overdensity significance (rejected because KDE sometimes assigns high significance to random Lockman-SWIRE locations).  
  > "Some studies (e.g., PlanckXXVII) have relied on kernel density estimator techniques to determine the statistical significance of spatial overdensities, which sometimes results in high significances for both overdense sources and random locations in the Lockman-SWIRE field." (3 sigma spatial overdensities)
- Alternative: Convolutional neural networks (CNNs) trained directly on SPIRE images (rejected because small training sample size and unresolved galaxies prevented successful classification).  
  > "Due to the small training sample size and the unresolved nature of high-$z$ galaxies in SPIRE maps, we find that convolutional neural networks trained on images of sources struggle to successfully distinguish between lensed and non-lensed galaxies." (Feature selection)
- Alternative: SIDES 2 deg^2 simulation for testing PHz line-of-sight alignments (found to be too small in area to reproduce rare PHz peaks, motivating the 5000 deg^2 Negrello et al. 2017 analytic Monte Carlo simulation).  
  > "This is likely caused by the small size of the SIDES simulation, preventing it from reproducing the rare objects that make up the PHz catalogue; the 2151 PHz sources were found across 10,700 deg$^2$, meaning that their density is about 0.2 deg$^{-2}$, and thus a simulation at least as large as $10\,{\rm deg}^2$ would be needed to find comparably rare objects." (The nature of the PHz sources)
- How they decided it was enough: _not stated_
- Limitation (authors): SPIRE 3-band photometric redshifts have large uncertainties (delta z ~ 1) due to the dust temperature-redshift degeneracy and cannot distinguish physical protoclusters at a single redshift from line-of-sight projections in individual sources.  
  > "By comparing the SPIRE photometric redshifts of multiple galaxies detected within the same PHz source, we can attempt to quantify the presence of line-of-sight alignments within the PHz HELP sources, but we find that the SPIRE photometric redshifts are too imprecise ($\delta z \approx 1$) to distinguish between overdensities at a single redshift from random alignments along the line-of-sight." (Photometric redshifts and star-formation rates)
- Limitation (authors): Herschel-SPIRE maps of 9 of the 228 PlanckXXVII sources could not be recovered.  
  > "For comparison, we repeated all of our analyses on the 228 PlanckXXVII sources (although in practice, we were unable to recover the *Herschel*-SPIRE maps of nine of the sources)." (The Planck List of High-z Source Candidates)
- Limitation (authors): The unlensed galaxy training set is drawn from 45 SCUBA-2 protocluster candidate fields and could still contain undiscovered fainter lensed galaxies.  
  > "Although these sources are well studied, this does not guarantee that there are undiscovered lensed galaxies within these protocluster candidates." (Training and test sets)
- Caveat (inferred, ours): The ALMA 870 um confirmation of PLCK_G224.6-40.7 is shown only as a cutout image in Fig. 16 with no observational, calibration, or lens-modelling details provided in the paper.
- Caveat (inferred, ours): The training set for the neural network explicitly excludes unlensed galaxies with S350 or S500 > 100 mJy and lensed galaxies with peak flux <= 100 mJy, building a ~100 mJy flux boundary directly into the training labels.

## Reproducibility

- Data public (paper): All data used in the paper are publicly available from the ESA Herschel Science Archive and the HELP Data site, and candidate catalogues are provided in the Appendices.  
  > "All of the data used in this paper is publicly available. The PlanckXXVII SPIRE maps are available through the ESA Herschel Science Archive (<http://archives.esac.esa.int/hsa/whsa>). The wide-field HELP maps can be downloaded from the Herschel Extragalactic Legacy Project Data site (<http://hedam.lam.fr/HELP>)." (Data availability)
- Products in archive: _not stated_
- Code: _not stated_
- Missing: Custom source detection, simultaneous Gaussian PSF photometry, and band-merging code
- Missing: Exact list of the 187 PHz HELP source names (only the 51 overdense/red candidates and 8 lens candidates are tabulated in Appendix A)
- Missing: Exact list of the 388 unlensed training galaxies and PyTorch training script
- Missing: ALMA imaging pipeline and parameters for PLCK_G224.6-40.7 (2019.1.01155.S)
- Data volume (inferred): ~10-50 GB for HELP DR1 SPIRE maps, Planck HFI maps, and PlanckXXVII SPIRE cutouts; <5 GB for the single ALMA continuum dataset of G224.
- Score (inferred): 65/5, The Herschel-SPIRE and Planck data are public and the photometry, overdensity, SED fitting, and PyTorch neural network algorithms are described in detail with explicit thresholds and equations, though custom code, the full 187-source target list, and ALMA data reduction details are not provided.
- Rediscovery candidate: no, ALMA is only used to display a single 870 um confirmation cutout image of one lensed galaxy (PLCK_G224.6-40.7) with no ALMA quantitative measurements or reduction recipe; the core paper is a Herschel-SPIRE + Planck statistical and cataloguing study.

## Links

- Method: (cite: PlanckHerschel2015) (Defines the IN-region contour method, pixel-histogram noise measurement, 350-um-anchored band matching, overdensity contrast, and MBB parameters adopted in this work.)
- Method: (cite: Castignani2014) (Provides the Poisson photometric-redshift clustering probability formalism adapted in Section 5.1.2.)
- Method: (cite: Negrello2017) (Provides the analytic 545 GHz clump luminosity function and Monte Carlo simulation method used to test line-of-sight alignments in Section 6.1.)
- Related: Planck list of high-z source candidates (PHz)
- Related: Herschel Extragalactic Legacy Project (HELP)

## Checks

```json
{
 "quotes": 109,
 "quotes_ok": 109,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 18,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 93,
  "stated": 50,
  "rate": 0.538
 },
 "evidence_ok": true
}
```
