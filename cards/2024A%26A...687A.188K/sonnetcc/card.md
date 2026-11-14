# Recovering the gas properties of protoplanetary disks through parametric visibility modeling: MHO 6

`2024A&A...687A.188K` | Astronomy and Astrophysics 2024 | first author: Kurtovic, N. T. | arXiv: 2404.07349 | DOI: 10.1051/0004-6361/202449667

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: Can parametric visibility modeling of CO isotopologue line emission recover the gas properties (emission height, brightness temperature, stellar mass, geometry, disk size) of the compact disk around the very-low-mass star MHO 6, where image-based techniques struggle?  
  > "we explore the advantages and limitations of describing the properties of the gas surface-emitting layer with a parametric visibility-based modeling." (Introduction); "For these reasons, we chose to describe the disk morphology directly in the visibilities." (Introduction)
- Target **MHO 6**: coordinates _not stated_; z/distance 154 pc  
  > "located in the Taurus star-forming region at 154 pc (cite: gaia2021edr3)" (Introduction); distance from Gaia EDR3 (cite: gaia2021edr3)  
  > "located in the Taurus star-forming region at 154 pc (cite: gaia2021edr3)" (Introduction)

## Data provenance

- ALMA projects: 2018.1.00310.S
- bands: Band 7 (0.87 mm)  
  > "This work includes 0.87 mm observations of the disk around MHO 6." (Observations); "The dataset was obtained by ALMA in Band 7, as part of the project 2018.1.00310.S (PI: P. Pinilla)." (Observations)
- frequencies and spectral setup: Two continuum spectral windows, one 12CO J=3-2 window and one 13CO J=3-2 window; native channel width 244.1 kHz  
  > "one spectral window covering the molecular line $^{12}$CO J=3-2 transition" (Observations); "Compared to the native frequency resolution of the observation, we increased the channel width from 244.1 kHz to 576.7 kHz." (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 12CO cube beam 110x80 mas (PA 31.5 deg), about 16x12 au; 13CO cube beam 124x89 mas (PA 34.6 deg), about 18x13 au (robust 0.5, no taper)  
  > "Thus, the spatial resolution of each image cube is about $16\times12$ au and $18\times13$ au for $^{12}$CO and $^{13}$CO, respectively." (Observations); "The $^{13}$CO cube has a resolution of $124\times89$ mas with a position angle of $34.6\,$deg." (Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Project 2018.1.00310.S, PI P. Pinilla; data preparation previously published in Kurtovic et al. 2021  
  > "as part of the project 2018.1.00310.S (PI: P. Pinilla)" (Observations); "The self-calibration and data preparation process was already published in (cite: kurtovic2021)." (Observations)
- Line: 12CO J=3-2 (not stated)
- Line: 13CO J=3-2 (not stated)
- Other facility **Gaia EDR3**: Distance to MHO 6 (154 pc)  
  > "located in the Taurus star-forming region at 154 pc (cite: gaia2021edr3)" (Introduction)
- External data: Stellar luminosity L_star = 0.06 Lsun, used for the passively heated midplane temperature  
  > "By using $L_\star=0.06L_\odot$ from (cite: kurtovic2021), derived from (cite: Herczeg2014)" (4.2 Comparison of MHO6 with other sources) [from (cite: kurtovic2021), derived from (cite: Herczeg2014)]
- External data: Literature sample of disk emission surface heights, brightness temperatures and z/Hg values used for comparison with MHO 6  
  > "In Fig. [6](#fig:surf_height), we compare the elevation of the emitting surfaces of those disks to our measurement in MHO 6" (4.2 Comparison of MHO6 with other sources) [from (cite: Law2022a; Law2023)]
- External data: Stellar mass of about 0.2 Msun and spectral type M5.0 for MHO 6  
  > "an M5.0 star a mass of $M_\star\sim0.2\,M_\odot$ (cite: kurtovic2021; pegues2021)" (Introduction) [from (cite: kurtovic2021; pegues2021)]
- External data: Gas-to-dust size ratio and disk sizes measured from moment 0 with an elliptical aperture, compared with this work  
  > "we found values that are consistent with those measured from integrating the moment 0 emission with an elliptical aperture in (cite: kurtovic2021)" (3.1 Results) [from (cite: kurtovic2021)]
- Simulation/model as data: Synthetic model image cubes generated from the best-fit parametric models, reimaged with tclean for comparison with the data and residuals  
  > "Additional image cubes from synthetic models or residuals were reconstructed with the same `tclean` setup" (Observations)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 5.6.2  
  > "CASA 5.6.2" (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Self-calibration and data preparation published in Kurtovic et al. 2021 (details not repeated)  
  > "The self-calibration and data preparation process was already published in (cite: kurtovic2021)." (Observations)

### Imaging

- task: tclean (image cubes for visual reference only; fitting done in the visibility plane)  
  > "For visual reference, we generated image cubes of each line with the CASA task `tclean`" (Observations)
- deconvolver: _not stated_
- weighting robust: robust = 0.5  
  > "with a robust parameter of 0.5 to obtain a good balance between the sensitivity and the angular resolution" (Observations)
- uv taper: none  
  > "No visibility tapering was applied." (Observations)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Continuum-subtracted measurement sets used (method not given)  
  > "we averaged the continuum-subtracted measurement sets into $30$ s bins to reduce data volume" (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: 12CO regridded with cvel2 to 0.5 km/s channels (32 channels from -3.5 km/s); 13CO to 0.9 km/s channels (19 channels from -3.5 km/s)  
  > "redefining the channels to start from -3.5 km s$^{-1}$, with 0.5 km s$^{-1}$ of channel width to increase the S/N of the emission, using 32 channels in total." (Observations); "we started from -3.5 km s$^{-1}$ with 0.9 km s$^{-1}$ of channel width, using 19 channels in total" (Observations)
- final beam: 12CO 110x80 mas, PA 31.5 deg; 13CO 124x89 mas, PA 34.6 deg  
  > "The $^{13}$CO cube has a resolution of $124\times89$ mas with a position angle of $34.6\,$deg." (Observations)
- final rms: _not stated_

### Inherited from earlier work

- Self-calibration and data preparation of the 2018.1.00310.S data  
  > "The self-calibration and data preparation process was already published in (cite: kurtovic2021)." (Observations) [from (cite: kurtovic2021)]
- Visibility-fitting approach follows the continuum visibility modeling  
  > "we followed a similar approach as that applied to the continuum visibility modeling presented in (cite: Kurtovic2022)" (3 Methodology) [from (cite: Kurtovic2022)]
- Emission surface z(r) functional form and the pressure scale height / midplane temperature prescriptions follow Law et al.  
  > "was modeled with the same functional form as in (cite: Law2022a; Law2023) in the image plane" (4.2 Comparison of MHO6 with other sources); "As in (cite: Law2022a), we describe $H_g$ as a function of radii under the assumption of vertical hydrostatic equilibrium" (4.2 Comparison of MHO6 with other sources) [from (cite: Law2022a; Law2023)]
- Disk-like layered intensity combination (max of front/back) as in discminer  
  > "This assumption is also considered in similar frameworks, such as `discminer` (cite: Izquierdo2021)" (3.1 Elevation, intensity, and combination of emitting layers) [from (cite: Izquierdo2021)]

### Not stated but needed to reproduce (our reading)

- Self-calibration solution intervals, calibrators and the exact continuum-subtraction channel ranges (deferred to Kurtovic et al. 2021)
- Flux calibrator and flux scale uncertainty for the dataset
- Prior ranges (lower/upper bounds) of every free parameter and the MCMC starting positions
- Number of free parameters and hence the actual walker count
- Size of the nest region in au and the field of view used for the nominal image relative to disk center
- Rest frequencies adopted for 12CO and 13CO J=3-2 and the velocity reference frame/convention
- Code of the authors' parametric visibility model (only the eddy/wrinkleology coordinate functions and galario are public)
- How the Rayleigh-Jeans brightness temperature conversion handled beam/pixel solid angle for the profiles
- Number of antennas, array configurations and on-source time
- Noise per channel adopted in the likelihood

## Analysis recipe

1. **Prepare per-channel visibilities**: Time-average continuum-subtracted self-calibrated data to 30 s, regrid channels with cvel2, extract each channel's visibility table in wavelength units  
  > "we averaged the continuum-subtracted measurement sets into $30$ s bins to reduce data volume" (Observations); "The visibility table of each channel was extracted and converted to wavelength units using each channel central frequency." (Observations)
   - software: CASA 5.6.2, cvel2
   - parameter: 12CO: 32 channels of 0.5 km/s starting at -3.5 km/s; 13CO: 19 channels of 0.9 km/s starting at -3.5 km/s  
  > "redefining the channels to start from -3.5 km s$^{-1}$, with 0.5 km s$^{-1}$ of channel width to increase the S/N of the emission, using 32 channels in total." (Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Build parametric channel-by-channel disk model**: Two emitting layers (front and back) with exponentially tapered power-law height and intensity, Keplerian velocity with Gaussian line broadening, layers combined by taking the maximum, plus a Gaussian cloud absorption term  
  > "Two emitting layers are calculated for each line: front (upper) and back (bottom), one on each side of the midplane." (3.1 Elevation, intensity, and combination of emitting layers); "we assume that the intensity value of each pixel in the model image is the maximum between upper and lower emission surface" (3.1 Elevation, intensity, and combination of emitting layers)
   - software: eddy, wrinkleology
   - parameter: Front and back layer heights imposed equal (z_b = -z_f); four free height parameters (z_f0, psi, phi, r_z)  
  > "we imposed the front and back layer should have the same height ($z_b=-z_f$) relative to the disk midplane" (3.1 Elevation, intensity, and combination of emitting layers)
   - parameter: Cloud absorption Gaussian with three free parameters: velocity center, width, amplitude  
  > "the velocity center ($c_{v0}$), the velocity width ($c_\sigma$), and the amplitude of the absorption ($c_a$)" (3.1 Elevation, intensity, and combination of emitting layers)
   - assumption: Purely Keplerian velocity field; Gaussian local line broadening  
  > "In the current model, the velocity field is approximated to be purely Keplerian" (3.1 Elevation, intensity, and combination of emitting layers); "we assumed a Gaussian line-broadening in the velocity" (3.1 Elevation, intensity, and combination of emitting layers)
   - assumption: Optically thick front layer over the whole channel velocity width  
  > "which is a first approximation for an optically thick front layer over the whole channel velocity width" (3.1 Elevation, intensity, and combination of emitting layers)
   - fitting: _not stated_
   - validation: Alternative smooth power-law layer combination tested; no significant improvement  
  > "This alternative did not produce significant improvements over the fitting" (3.1 Elevation, intensity, and combination of emitting layers)
3. **Generate nested model images and compute model visibilities**: Nominal image plus higher-resolution nest in the center, averaged down to the nominal pixel size and inserted; visibilities computed with galario  
  > "To combine both, we averaged the pixels of the nest image to match the pixel size of the nominal, creating a “reduced” image." (3.2 Nesting images); "we used the `galario` package (cite: Tazzari2017) to calculate the visibilities of the model" (3 Methodology)
   - software: galario
   - parameter: Nominal image 512 px at 15 mas; inner 64 px replaced by nest of level n=2 (4^2 oversampling)  
  > "For MHO 6, we used a nominal image of 512 px in size, with each pixel being 15 mas." (3.2 Nesting images); "The inner 64 pixels of the nominal image are replaced by a nest image of level" (3.2 Nesting images)
   - fitting: _not stated_
   - validation: Flux conservation of nested models compared with an n=6 reference over n=0..6 and 256 disk-center offsets  
  > "We generated models from $n=0$ (no nesting) to $n=6$ (oversample each nominal pixel with $4^6$ pixels), and took the model images with $n=6$ as the reference for true flux." (Appendix: Nesting images); "This gave us a grid of 256 models per level of nesting." (Appendix: Nesting images)
4. **Fit 12CO and 13CO independently with MCMC**: emcee sampling of each line's parameters independently, to test consistency of shared parameters  
  > "We fitted both CO isotopologues independently, with the same parametric functions." (3.3 MCMC fitting)
   - software: emcee
   - parameter: Walkers = eight times the number of free parameters; last 10^5 steps used after a burn-in of at least 10^5 steps  
  > "using eight times the number of walkers with respect to the free parameters" (3.3 MCMC fitting); "Each model results are sampled from the last $10^5$ steps, after a burning period of at least $10^5$ steps." (3.3 MCMC fitting)
   - assumption: Flat uniform priors, wide enough that walkers do not reach the bounds  
  > "Each parameter has a flat uniform prior over the allowed parameter range, which extends far enough so that the walkers do not interact with it." (3.3 MCMC fitting)
   - fitting: emcee MCMC, flat uniform priors; likelihood not stated  
  > "Each parameter has a flat uniform prior over the allowed parameter range" (3.3 MCMC fitting)
   - validation: Consistency of shared parameters between independent 12CO and 13CO fits; comparison with literature stellar mass; residual cubes and moment maps  
  > "Both CO isotopologues find consistent solutions for the shared parameters" (4 Results); "and also with the literature (cite: wardduong2018; kurtovic2021; pegues2021)" (4 Results)
5. **Derive brightness temperature, disk radii and absorption-corrected fluxes from the best models**: Convert model intensity to brightness temperature with Rayleigh-Jeans; measure radii enclosing 68, 90 and 95 percent of the front-layer flux; correct fluxes for cloud absorption  
  > "This was done under the Rayleigh-Jeans approximation for black body emission in the low frequency regime, assuming the emission is entirely optically thick." (4 Results); "The size of the disk is measured by constraining the radii enclosing $68\%$, $90\%$, and $95\%$ of the total flux as measured from the front layer emission surface." (4 Results)
   - assumption: Emission entirely optically thick for the brightness temperature conversion  
  > "assuming the emission is entirely optically thick" (4 Results)
   - fitting: _not stated_
   - validation: Disk sizes compared with moment-0 elliptical-aperture sizes from Kurtovic et al. 2021  
  > "we found values that are consistent with those measured from integrating the moment 0 emission with an elliptical aperture in (cite: kurtovic2021)" (4 Results)
6. **Compare emission height and temperature with other disks via scale height**: Compute pressure scale height Hg for three midplane temperature prescriptions (front-layer temperature, constant 20 K, passively heated flared disk) and compare z/Hg and z(r) to the Law et al. sample  
  > "we calculate three different $H_g$ as a function of radii, by considering different descriptions for the midplane temperature" (4.2 Comparison of MHO6 with other sources)
   - parameter: Flaring angle phi = 0.02; L_star = 0.06 Lsun  
  > "where $\varphi$ is the flaring angle, which we set to 0.02 for comparison with the literature" (4.2 Comparison of MHO6 with other sources); "By using $L_\star=0.06L_\odot$ from (cite: kurtovic2021), derived from (cite: Herczeg2014)" (4.2 Comparison of MHO6 with other sources)
   - assumption: Vertical hydrostatic equilibrium; midplane temperature from three prescriptions  
  > "we describe $H_g$ as a function of radii under the assumption of vertical hydrostatic equilibrium" (4.2 Comparison of MHO6 with other sources)
   - fitting: _not stated_
   - validation: _not stated_
7. **Choose nesting level from flux-loss test**: Compare flux loss of nested models in the inner 10 au to per-channel sensitivity  
  > "Increasing the nesting level from $n=0$ to $n=2$ leads to a decrease in flux loss from 20% to 2%" (4.4 How much nesting is needed)
   - fitting: _not stated_
   - validation: Flux loss below the per-channel noise and the profile noise level  
  > "Thus, the flux loss is below $0.5\sigma$ per channel" (4.4 How much nesting is needed)

## Software

- **CASA** 5.6.2: Time averaging, channel regridding (cvel2) and tclean imaging  
  > "CASA 5.6.2" (Observations); "We applied the task `cvel2` to the self-calibrated and time-binned" (Observations)
- **galario** : Computing model visibilities from model images  
  > "we used the `galario` package (cite: Tazzari2017) to calculate the visibilities of the model" (3 Methodology)
- **eddy** : Disk coordinate system functions (emission surface geometry)  
  > "Those coordinates were calculated based on the functions from the python package `eddy` (cite: eddy)" (3.1 Elevation, intensity, and combination of emitting layers)
- **wrinkleology** : GitHub repository organizing eddy functions for image cube generation  
  > "which are organized for image cube generation in the `git-hub` repository `wrinkleology` (cite: simpledisk)" (3.1 Elevation, intensity, and combination of emitting layers)
- **emcee** : MCMC sampling of model parameters  
  > "We sampled each parameter density distribution with the Markov chain Monte Carlo (MCMC) code `emcee` (cite: emcee2013)" (3.3 MCMC fitting)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Stellar mass from 12CO fit | 0.164 | +/-0.003 | Msun | 4 | The $^{12}$CO emission constrains $M_\star=0.164\pm0.003$ |
| Stellar mass from 13CO fit | 0.171 | +0.009/-0.010 | Msun | 4 | $0.171_{-0.010}^{+0.009}$ |
| Inclination (12CO) | 59.1 | +2.8/-0.5 | deg | 4 | $59.1_{-0.5}^{+2.8}$ |
| Position angle (12CO) | 293.5 | +0.2/-0.3 | deg | 4 | $293.5_{-0.3}^{+0.2}$ |
| Absorption-corrected 12CO flux F_corr | 9.68 | +0.46/-0.38 | mJy km/s | 5 | $9.68_{-0.38}^{+0.46}$ |
| 12CO R68% | 131.2 | +1.9/-1.8 | au | 5 | $131.2_{-1.8}^{+1.9}$ |
| 12CO R90% | 182.3 | +/-3.0 | au | 5 | $182.3_{-3.0}^{+3.0}$ |
| 12CO R95% | 203.6 | +3.2/-3.3 | au | 5 | $203.6_{-3.3}^{+3.2}$ |
| Back-layer 12CO brightness temperature within 100 au | 18 | +/-1 | K | 5 | the brightness temperature of the back layer maintains a nearly constant value of $18\pm1$ K within the first 100 au of $^{12}$CO emission |
| 12CO brightness temperature at 100 au | 17 | +/-1 | K | 5 | At 100 au, the brightness temperature of the $^{12}$CO emission is $17\pm1$ K |
| Gas-to-dust size ratio (0.87 mm vs 12CO) | 3.9 | not stated | dimensionless | 5 | we confirm the gas to dust size ratio of 3.9 when comparing the 0.87 mm emission to the $^{12}$CO J=3-2 emission |
| Minimum cloud transparency, 12CO | 50% | not stated | percent | 4 | the $^{12}$CO emission has the lowest transparency of $50\%$ at the central velocity channel |
| Minimum cloud transparency, 13CO | approximately 70% | not stated | percent | 4 | the lowest transparency being approximately $70\%$ at the central velocity of the disk |
| z/Hg of the 12CO emitting layer | 1 to 3 (average about 2) | not stated | dimensionless | 6 | we find that $z/H_g$ ranges from $1$ to $3\times H_g$ |
| Alternative layer-combination parameters (12CO) | mu = 0.355, gamma = 0.3 | +/-0.04 (mu), +/-0.05 (gamma) | mJy/px (mu); dimensionless (gamma) | 2 | The best results were $\mu=0.355\pm0.04$ mJy/px and $\gamma=0.3\pm0.05$ |
| Inner-10-au flux loss for 12CO, n=0 to n=2 | 20% to 2% (0.2 Jy to 0.022 Jy) | not stated | percent | 7 | Increasing the nesting level from $n=0$ to $n=2$ leads to a decrease in flux loss from 20% to 2%, which is about 0.022 Jy for the inner 10 au. |

## Qualitative findings

- 12CO and 13CO fits return consistent stellar mass, geometry and central velocity  
  > "the models return the same consistent results for the stellar mass, disk geometry, and central velocity" (abstract)
- MHO 6 has among the most elevated emission surfaces, consistent with predictions for very-low-mass stars  
  > "MHO 6 surface height is among the most elevated surfaces, consistent with the predictions for disks around very-low-mass stars" (abstract)
- No robust detection of an emission cavity in CO  
  > "do not find robust conclusive evidence of an emission cavity, at least at the sensitivity and resolution of the observations" (5.1 Morphology of MHO6 CO isotopologues emission)
- Low-contrast X-shaped non-axisymmetric residuals in 12CO, taken as an incomplete treatment of front/back layer interaction  
  > "Detecting this “X” residual suggests an incomplete description of the interaction between emission from the front and back layer" (5.1 Morphology of MHO6 CO isotopologues emission)

## Claim tuples

- H: Parametric visibility modeling can recover the stellar mass, geometry and central velocity of a compact disk from moderate-resolution CO data | E: Independent MCMC fits of 12CO and 13CO J=3-2 visibilities of MHO 6 | R: 12CO gives M_star=0.164+/-0.003 Msun and 13CO gives 0.171 Msun; geometry and VLSR consistent between lines | F: The method returns consistent, literature-matching parameters even for the faint 13CO | **supported**
- H: The emitting surface of a disk around a very-low-mass star is more elevated than around higher-mass stars | E: Compare modeled z(r) of MHO 6 with the Law et al. sample using the same functional form | R: MHO 6 is among the most elevated surfaces within the first 50 au, with z/r above 0.3 for 12CO out to 100 au | F: Consistent with models predicting geometrically thicker disks around very-low-mass stars | **supported**
- H: The model can separate front and back layers to give brightness temperatures | E: Convert model intensity of each layer to Rayleigh-Jeans brightness temperature | R: Back-layer 12CO temperature of 18+/-1 K within 100 au | F: Consistent with CO freeze-out and a cold midplane with T<20 K | **partially**
- H: A nested-image oversampling of the inner disk keeps flux fidelity without prohibitive pixel size | E: Compare nested models n=0..6 against an n=6 reference | R: Inner-10-au flux loss drops from 20% to 2% going from n=0 to n=2 | F: n=2 is adequate for MHO 6 (below 0.5 sigma per channel) | **supported**

## Reasoning

- Why this data: MHO 6 is spatially resolved in dust and 12CO at 15 au resolution and has a large dust gap around a very-low-mass star  
  > "MHO 6 was chosen as it is spatially resolved in dust continuum and $^{12}$CO J=3-2 emission when observed with 15 au resolution." (Introduction)
- Why this method: Moderate brightness and small angular extent make the source unsuitable for image-plane analysis  
  > "Due to its moderate brightness and relatively small angular extent, MHO 6 is not an ideal source to be studied in the image plane" (Introduction)
- Alternative: Smooth power-law weighting of front and back layers instead of the binary maximum; rejected for no significant improvement  
  > "This alternative did not produce significant improvements over the fitting" (3.1 Elevation, intensity, and combination of emitting layers)
- How they decided it was enough: Nesting level chosen so that flux loss is below single-channel sensitivity  
  > "The acceptable flux loss should be decided on the basis of a comparison with an observation’s sensitivity, such that the dominant uncertainty source is the single channel sensitivity and not the model’s flux loss." (4.4 How much nesting is needed)
- Limitation (authors): Model ignores midplane absorption of back-layer emission, which could lower the observed brightness temperature  
  > "We note that our model does not consider possible absorption in the midplane to the emission from the back layer, which could be lowering the observed brightness temperature." (5.1 Morphology of MHO6 CO isotopologues emission)
- Limitation (authors): Brightness temperature highly uncertain inside 10 au  
  > "becomes highly uncertain for $r<10$ au in both CO isotopologues, due to the limited angular resolution and fitted velocity range" (5.1 Morphology of MHO6 CO isotopologues emission)
- Limitation (authors): Spatial masking is not possible in visibility modeling  
  > "Masking spatial regions is not possible with visibility modeling." (5.3 Advantages of image- versus visibility-based analysis)
- Caveat (inferred, ours): Single source and single dataset; no injection-recovery test of the visibility model on synthetic data with known parameters
- Caveat (inferred, ours): Optical depth of 12CO is assumed fully thick, so brightness temperatures are lower limits on kinetic temperature
- Caveat (inferred, ours): Front and back layer heights forced equal; the 13CO turnover parameters are unconstrained
- Caveat (inferred, ours): Likelihood and noise treatment are not described

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Code: eddy and wrinkleology coordinate functions are public; release of this paper's own visibility-fitting code is not stated  
  > "for making them available for public use" (Acknowledgments)
- Missing: Prior bounds, starting points and likelihood definition for the MCMC
- Missing: Self-calibrated measurement sets (self-calibration recipe is in Kurtovic et al. 2021, not here)
- Missing: The authors' model code
- Missing: Exact nest field of view and cell definitions beyond the stated 512 px / 64 px / n=2
- Data volume (inferred): Likely tens of GB for the raw ALMA Band 7 measurement sets; a few GB after 30 s averaging of the line spectral windows
- Score (inferred): 3/5, Public ALMA project code and a clear model description with a final parameter table, but self-calibration, priors, likelihood and the fitting code are not given in the paper.
- Rediscovery candidate: no, Data public status not stated in the paper, and the fitting code, priors and self-calibration recipe are missing, so a full redo is not feasible from the text alone.

## Links

- Method: Kurtovic et al. 2022 (cite: Kurtovic2022) (Continuum visibility modeling approach followed here)
- Method: Tazzari et al. 2017 (cite: Tazzari2017) (galario package used for model visibilities)
- Companion: Kurtovic et al. 2021 (cite: kurtovic2021) (Published the self-calibration and data preparation of the same dataset and earlier MHO 6 results)
- Companion: Law et al. 2022 (cite: Law2022a) (Comparison sample and Hg/temperature prescriptions)

## Checks

```json
{
 "quotes": 109,
 "quotes_ok": 109,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 16,
 "numeric_problems": 0,
 "fill": {
  "facts": 99,
  "stated": 66,
  "rate": 0.667
 },
 "evidence_ok": true
}
```
