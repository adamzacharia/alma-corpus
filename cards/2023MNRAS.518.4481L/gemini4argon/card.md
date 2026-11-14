# Dynamical mass measurements of two protoplanetary discs

`2023MNRAS.518.4481L` | Monthly Notices of the Royal Astronomical Society 2023 | first author: Lodato, G. | arXiv: 2211.03712 | DOI: 10.1093/mnras/stac3223

Card schema 1.0 | model gemini-4-argon | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks, star_formation
- Question: Measure dynamically the total disc mass of IM Lup and GM Aur from deviations from Keplerianity in $^{12}$CO and $^{13}$CO rotation curves induced by disc self-gravity and pressure gradients.  
  > "measure deviations from Keplerianity induced by the disc self-gravity, thus constraining the total disc mass with good accuracy and independently on mass conversion factors between the tracer used and the total mass." (Abstract); "Here, we refine our methodology and extend it to two additional sources, GM Aur and IM Lup, for which archival line observations are available for both the $^{12}$CO and the $^{13}$CO line." (Abstract)
- Target **IM Lup**: coordinates _not stated_; z/distance 158 pc  
  > "It is a K5 star, located at a distance of 158 pc (cite: Gaia18)" (IM Lup); "| $d$ (pc) | 158 | 159 |" (Table 1); distance from (cite: Gaia18) / (cite: Oberg21)  
  > "It is a K5 star, located at a distance of 158 pc (cite: Gaia18)" (IM Lup); "| $d$ (pc) | 158 | 159 |" (Table 1)
- Target **GM Aur**: coordinates _not stated_; z/distance 159 pc  
  > "GM Aur is another well-known disc, at a distance of 159 pc (cite: Gaia18)." (GM Aur); "| $d$ (pc) | 158 | 159 |" (Table 1); distance from (cite: Gaia18) / (cite: Oberg21)  
  > "GM Aur is another well-known disc, at a distance of 159 pc (cite: Gaia18)." (GM Aur); "| $d$ (pc) | 158 | 159 |" (Table 1)

## Data provenance

- ALMA projects: 2018.1.01055.L
- bands: _not stated_
- frequencies and spectral setup: 12CO (2-1) and 13CO (2-1) with spectral resolution 0.1 km/sec and 0.2 km/sec respectively, and velocity sampling of 0.2 km/sec  
  > "In this paper we will use the $^{12}$CO (2-1) and $^{13}$CO (2-1) observations of IM Lup, recently observed within the ALMA Large Program MAPS (cite: Oberg21), with a spatial resolution of $\approx 0.15$” and a spectral resolution of 0.1 km/sec and 0.2 km/sec respectively, and velocity sampling of 0.2 km/sec (cite: Oberg21)" (IM Lup); "MAPS data, with a spatial resolution of $\approx 0.15$” and a spectral resolution of 0.1 km/sec and 0.2 km/sec for $^{12}$ and $^{13}$CO respectively, and velocity sampling of 0.2 km/sec" (GM Aur)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~ 0.15"  
  > "recently observed within the ALMA Large Program MAPS (cite: Oberg21), with a spatial resolution of $\approx 0.15$”" (IM Lup); "MAPS data, with a spatial resolution of $\approx 0.15$”" (GM Aur)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: archival (ALMA Large Program MAPS)  
  > "archival line observations are available for both the $^{12}$CO and the $^{13}$CO line." (Abstract); "In this paper we will use the $^{12}$CO (2-1) and $^{13}$CO (2-1) observations of IM Lup, recently observed within the ALMA Large Program MAPS (cite: Oberg21)" (IM Lup)
- Line: 12CO 2-1 (not stated)
- Line: 13CO 2-1 (not stated)
- External data: Distances and inclinations of IM Lup (d=158 pc, i=47.5 deg) and GM Aur (d=159 pc, i=53.2 deg)  
  > "Distances and inclinations of the two sources are obtained from the literature. In particular, we adopt the same geometrical parameters as used in MAPS (cite: Oberg21)" (Basic system parameters); "| $i$ (degrees) | 47.5$^\circ$ | 53.2$^\circ$ |" (Table 1) [from (cite: Gaia18); (cite: Oberg21)]
- External data: Pressure scale height parameters H0 and q for IM Lup (H0=10 au, q=0.66) and GM Aur (H0=7.5 au, q=0.3)  
  > "we fix the pressure scale height from the thermochemical model of (cite: Zhang21) (which are in very good agreement with the recent analysis of (cite: Paneque22))" (Basic system parameters); "| $H_0$ (au) | 10 | 7.5 |" (Table 1) [from (cite: Zhang21)]
- External data: Height of emitting layers of 12CO and 13CO (z0, p, q, Rt) and 2D gas temperature parameterizations for GM Aur  
  > "and the height of the emitting layers of $^{12}$CO and $^{13}$CO from the MAPS analysis (cite: Law21)." (Basic system parameters); "(cite: Law21) parameterize the gas temperatures of the two molecules as:" (GM Aur) [from (cite: Law21)]
- External data: Dust mass of IM Lup (1.7e-3 M_sun)  
  > "Note that, given the known value of the dust mass of $M_{\rm dust}=1.7~10^{-3}\, \mathrm{M}_{\ensuremath{\odot}}$ (cite: Cleeves16), our measurement implies a gas/dust ratio of $\sim 60$, close to the standard assumed value of 100." (IM Lup) [from (cite: Cleeves16)]
- External data: Dust mass of GM Aur (0.002 M_sun)  
  > "The dust mass estimated by (cite: Macias18) is $0.002\, \mathrm{M}_{\ensuremath{\odot}}$, which would translate into $0.2\, \mathrm{M}_{\ensuremath{\odot}}$ for the gas mass, assuming a gas/dust ratio of 100." (GM Aur) [from (cite: Macias18)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Delivered data products from the MAPS survey used directly  
  > "(Note that, as mentioned by (cite: Oberg21) “For the delivered data products the velocity resolutions have been coarsened to achieve more uniformity between spectral-line cubes as described in (cite: Czekala21)”)." (IM Lup); "The kinematical data of the CO molecules used in this paper are publiclly avaiable from the MAPS survey <https://alma-maps.info/data.html>." (Data Availability)
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
- final beam: ~ 0.15"  
  > "recently observed within the ALMA Large Program MAPS (cite: Oberg21), with a spatial resolution of $\approx 0.15$”" (IM Lup)
- final rms: _not stated_

### Inherited from earlier work

- Dynamical disc mass fitting methodology from rotation curves including self-gravity  
  > "In (cite: Veronesi21) we have demonstrated a proof-of-concept method that is based on a precise determination of the rotation curve of the disc, from which we can obtain *a dynamical measurement* of the disc mass" (Introduction); "We had previously used the same method to determine the mass of the disc in Elias 2-27 (cite: Veronesi21) and here we thus extend the same analysis to two additional sources." (Conclusions) [from (cite: Veronesi21)]
- Calibration and imaging of spectral-line cubes from the MAPS survey  
  > "“For the delivered data products the velocity resolutions have been coarsened to achieve more uniformity between spectral-line cubes as described in (cite: Czekala21)”" (IM Lup) [from (cite: Oberg21); (cite: Czekala21)]
- EDDY Simple Harmonic Oscillator (SHO) rotation curve extraction and line centroid fitting methods  
  > "To extract the rotation curves of IM Lup and GM Aur using EDDY (cite: teague2019eddy), we followed the method presented in (cite: teague2018kinematical) and in (cite: teague2018evidence)." (EDDY - Simple Harmonic Oscillator (SHO)); "For a thorough explanation of these methods, see (cite: teague2018robust)." (EDDY - Simple Harmonic Oscillator (SHO)) [from (cite: teague2018kinematical); (cite: teague2018evidence); (cite: teague2018robust)]
- DISCMINER rotation curve extraction and lower surface masking method  
  > "To test the robustness of our model we obtained the rotation curves of the two sources using both EDDY (cite: teague2019eddy) and DISCMINER (cite: Izquierdo21), each of which has got its advantages and drawbacks." (Extracting the rotation curve) [from (cite: Izquierdo21)]

### Not stated but needed to reproduce (our reading)

- Position angle (PA) values for IM Lup and GM Aur (referred to in text as being in Table 1, but omitted from Table 1)
- Which specific MAPS image cube data products (e.g., robust weighting, multiscale vs JvM-corrected cubes) were downloaded from the MAPS repository
- Radial bin width / step size used when extracting rotation curves in EDDY and DISCMINER
- Exact grid resolution and radial/vertical domain bounds used for the 2D (R, Z) numerical integration grid of the self-gravitating potential term

## Analysis recipe

1. **Extract rotation curves using EDDY (Simple Harmonic Oscillator method)**: Fit line centroids using Gaussian and Quadratic methods and align spectra in annuli with a Simple Harmonic Oscillator (SHO) model deprojected using known disc inclination, position angle, and emitting layer height z(R).  
  > "There are different methods to fit the line centroids, and in this work we have used the so-called Quadratic method and the Gaussian method, each of them showing pros and cons." (EDDY - Simple Harmonic Oscillator (SHO)); "More generally, the Simple Harmonic Oscillator (SHO) method implemented in EDDY is able to also obtain the radial velocity by modelling the velocity shift as" (EDDY - Simple Harmonic Oscillator (SHO)); "We extracted the rotation curves from an inner radius equals to the beam FWHM to an outer radius of $\sim 500$ au for IM Lup in the $^{12}\mathrm{CO}$ line and $\sim$ 400 au for GM Aur in both lines and IM Lup in the $^{13}\mathrm{CO}$ line" (EDDY - Simple Harmonic Oscillator (SHO))
   - software: EDDY
   - parameter: Radial range: from beam FWHM to ~500 au (IM Lup 12CO) and ~400 au (GM Aur both lines and IM Lup 13CO)  
  > "We extracted the rotation curves from an inner radius equals to the beam FWHM to an outer radius of $\sim 500$ au for IM Lup in the $^{12}\mathrm{CO}$ line and $\sim$ 400 au for GM Aur in both lines and IM Lup in the $^{13}\mathrm{CO}$ line" (EDDY - Simple Harmonic Oscillator (SHO))
   - parameter: Line centroid methods: Gaussian and Quadratic  
  > "There are different methods to fit the line centroids, and in this work we have used the so-called Quadratic method and the Gaussian method, each of them showing pros and cons." (EDDY - Simple Harmonic Oscillator (SHO))
   - assumption: Axisymmetric disc with thin emitting layer z_i(R) and fixed geometry from Table 1  
  > "Considering an axisymmetric disc, we expect the spectra to have the same shape (i.e., peak and width), but to have their line centers shifted by the velocity of the disk, projected along the line of sight ($v_\text{los}$)." (EDDY - Simple Harmonic Oscillator (SHO)); "Note that $\phi$ and $R$ are retrieved from any projected location by assuming a thin emitting layer, with height $z(R)$." (EDDY - Simple Harmonic Oscillator (SHO))
   - fitting: Fit systemic, azimuthal, and radial velocities in each annulus using SHO model  
  > "The systemic velocity is fitted as well as the azimuthal and radial ones." (EDDY - Simple Harmonic Oscillator (SHO))
   - validation: Visual inspection of velocity-azimuth alignment plots and comparison with DISCMINER curves; EDDY rejected for GM Aur due to lower surface contamination.  
  > "for the more challenging case of GM Aur, the contamination from the back side does not allow to use EDDY and for this source we only use the DISCMINER rotation curves." (Rotation curves: results)
2. **Extract rotation curves using DISCMINER**: Fit Gaussian or quadratic profiles to line profiles to obtain line-of-sight velocities, model and mask the lower emitting surface, and compute unweighted azimuthal averages of deprojected velocities within [-30, 30] deg around the disc major axis.  
  > "Also DISCMINER , like EDDY , can obtain the velocity by fitting either a Gaussian or a quadratic form to the line profile." (DISCMINER); "DISCMINER, however, is able to model and identify the projected location of the disc lower surface to produce azimuthal masks and remove from the analysis those portions of the disc that are more likely affected by the contribution of this surface" (DISCMINER); "We find that the deprojected velocities, obtained through Eq. (\[eq:andres\]), do not suffer from strong azimuthal gradients owing to the contribution of the lower emission surface within an azimuthal section of \[-30, 30\] deg around the major axes of the discs." (DISCMINER)
   - software: DISCMINER
   - parameter: Azimuthal averaging window: [-30, 30] deg around major axes  
  > "within an azimuthal section of \[-30, 30\] deg around the major axes of the discs. It is in this region where azimuthal unweighted averages of the deprojected velocities are then computed, as a function of radius" (DISCMINER)
   - assumption: Radial and vertical velocity components v_R and v_z are negligible or localised; fixed orientation and emission surfaces from Table 1  
  > "This expression assumes that both the radial and vertical components of the velocity field, $v_R$ and $v_z$, are either negligible or localised such that they do not contribute systematically to the observed deviations from Keplerian rotation over large spatial scales." (DISCMINER)
   - fitting: Gaussian and quadratic fits to pixel line profiles followed by unweighted azimuthal averaging  
  > "Also DISCMINER , like EDDY , can obtain the velocity by fitting either a Gaussian or a quadratic form to the line profile." (DISCMINER)
   - validation: Compared against EDDY rotation curves and compared Gaussian vs Quadratic line profile methods  
  > "In Figure 1 (upper panels) we compare the rotation curves obtained for IM Lup using EDDY (red and grey lines, referring to the different methods to extract the line centroid, see legend), with the one extracted with DISCMINER (blue line)." (Rotation curves: results)
3. **Pre-compute self-gravitating potential contribution on a 2D grid**: Numerically integrate the 1D integral for the radial derivative of the disc gravitational potential (Eq. 14) on a 2D grid (R, Z) using QUADPACK and interpolate at (R, z(R)) during MCMC fitting.  
  > "To do so, we used QUADPACK, a Fortran library for numerical integration of one-dimensional functions (cite: quadpack). In particular, we used a quadratic method of integration." (Numerical integration of the self-gravitating term); "Since the integration is computationally consuming, we integrated Eq. (\[sgterm\]) on a two-dimensional grid (R,Z) and then, at each step of the fitting procedure, we interpolate the self-gravitating term from the grid, according to the value of $(R,z(R))$." (Numerical integration of the self-gravitating term)
   - software: QUADPACK, DySc
   - parameter: Surface density power-law index gamma = 1  
  > "In the following, we will fix $\gamma=1$." (Disc radial and vertical structure)
   - assumption: Tapered power-law surface density profile with gamma = 1  
  > "We assume that the disc surface density is described as a tapered power law, following the similarity solutions of (cite: Lyndenbellpringle):" (Disc radial and vertical structure)
   - fitting: _not stated_
   - validation: _not stated_
4. **Fit dynamical model to 12CO and 13CO rotation curves via MCMC**: Simultaneously (and for GM Aur also separately) fit 12CO and 13CO rotation curves to the analytical + numerical rotation velocity model including stellar gravity, disc self-gravity, radial pressure gradient, and emitting height z(R) using emcee.  
  > "Our model rotation curve is given by Eqs. (\[eq:rotcurve\]) and (\[eq:sgpot\]) and depends on three free parameters: the stellar mass $M_\star$, the disc mass $M_{\rm d}$ and the scale radius $R_{\rm c}$." (Results); "We then fit simultaneously both isotopologues with the same model using standard Monte Carlo Markov Chains techniques, as implemented in emcee (cite: foreman13)." (Results)
   - software: emcee, DySc, corner, MATPLOTLIB
   - parameter: 100 walkers, 1500 burn-in steps, 500 production steps  
  > "We use 100 walkers, with 1500 steps as burn-in and 500 steps to evaluate confidence intervals." (Results)
   - parameter: Reference radius R0 = 100 au; fixed parameters from Table 1  
  > "As reference radius, we choose $R_0=100$ au. Table 1 shows the values that we assume for all the parameters mentioned in this section." (Basic system parameters)
   - assumption: Vertically isothermal disc in hydrostatic and centrifugal balance; independent data points along the rotation curve; gas-to-dust ratio evaluated against literature dust masses  
  > "For what concerns the vertical disc structure, we assume that the disc is vertically isothermal and that the density and pressure profiles are given by:" (Disc radial and vertical structure); "Note that in the fitting procedure we have neglected the fact that the measurement points of the rotation curve are not fully independent." (IM Lup)
   - fitting: MCMC sampler (emcee) with 100 walkers, 1500 burn-in steps, 500 steps; uniform initialization in M_* in [1, 1.5] M_sun, M_d in [0.05, 1] M_sun, R_c in [100, 300] au; uniform priors M_* in [0, 2] M_sun, M_d > 0 M_sun, R_c in [50, 800] au.  
  > "We initialize the MCMC search by assuming a uniform distribution of the three parameters within the following intervals: $M_\star/\text{M}_\odot\in [1,1.5]$, $M_{\rm d}/\text{M}_\odot\in [0.05,1]$, $R_{\rm c}/\mbox{au}\in [100,300]$." (Results); "We use 100 walkers, with 1500 steps as burn-in and 500 steps to evaluate confidence intervals. The priors are uniform with $M_\star/\text{M}_\odot\in [0,2]$, $M_{\rm d}/\text{M}_\odot>0$, $R_{\rm c}/\mbox{au}\in [50,800]$." (Results)
   - validation: Tested sensitivity to H0/R0 in range [0.08, 0.25] for IM Lup; compared Gaussian vs Quadratic centroid fits; tested 2D temperature stratification effect for GM Aur.  
  > "We explore a relatively wide range in values for $H_0/R_0$, from 0.08 up to 0.25, that we believe bracket sensible values." (Dependence on $H/R$); "We have also attempted to fit the data obtained by using the quadratic method for both EDDY and DISCMINER ." (Using the quadratic method to retrieve the rotation curves); "In Fig. \[fig:dv\] we plot the difference between the two rotation curves obtained from DISCMINER (blue dots) and the expected difference due to the temperature stratification according to Eq. (\[eq:Tstrat\]) (orange line)." (GM Aur)

## Software

- **EDDY** : Extracting disc rotation curves using the Simple Harmonic Oscillator (SHO) method with Gaussian and Quadratic line centroid fits  
  > "To test the robustness of our model we obtained the rotation curves of the two sources using both EDDY (cite: teague2019eddy) and DISCMINER (cite: Izquierdo21), each of which has got its advantages and drawbacks." (Extracting the rotation curve)
- **DISCMINER** : Extracting disc rotation curves and masking contamination from the lower emitting surface  
  > "To test the robustness of our model we obtained the rotation curves of the two sources using both EDDY (cite: teague2019eddy) and DISCMINER (cite: Izquierdo21), each of which has got its advantages and drawbacks." (Extracting the rotation curve); "DISCMINER, however, is able to model and identify the projected location of the disc lower surface to produce azimuthal masks and remove from the analysis those portions of the disc that are more likely affected by the contribution of this surface" (DISCMINER)
- **emcee** : MCMC fitting of the rotation curve model to constrain stellar mass, disc mass, and scale radius  
  > "We then fit simultaneously both isotopologues with the same model using standard Monte Carlo Markov Chains techniques, as implemented in emcee (cite: foreman13)." (Results); "We used the emcee algorithm (Foreman-Mackey et al. 2013), the corner package Foreman-Mackey (2016) to produce corner plots and python-based MATPLOTLIB package (Hunter 2007) for all the other figures." (Acknowledgements)
- **DySc** : Publicly available MCMC dynamical rotation curve fitting code ('DySc - Dynamical Scale')  
  > "The MCMC fitting procedure code we used is publicly available on GitHub “DySc - Dynamical Scale" [^3]" (Results)
- **QUADPACK** : Fortran library used for numerical integration of the 1D self-gravitating potential term  
  > "To do so, we used QUADPACK, a Fortran library for numerical integration of one-dimensional functions (cite: quadpack)." (Numerical integration of the self-gravitating term)
- **corner** : Producing MCMC posterior corner plots  
  > "We used the emcee algorithm (Foreman-Mackey et al. 2013), the corner package Foreman-Mackey (2016) to produce corner plots and python-based MATPLOTLIB package (Hunter 2007) for all the other figures." (Acknowledgements)
- **MATPLOTLIB** : Generating figures  
  > "We used the emcee algorithm (Foreman-Mackey et al. 2013), the corner package Foreman-Mackey (2016) to produce corner plots and python-based MATPLOTLIB package (Hunter 2007) for all the other figures." (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| IM Lup stellar mass (EDDY Gaussian) | 1.02 | not stated | M_sun | 4 | For EDDY , the best fit stellar mass is $M_\star\approx 1.02 \, \mathrm{M}_{\ensuremath{\odot}}$, the best fit disc mass is $M_{\rm d}\approx 0.096 \, \mathrm{M}_{\odot}$ and the scale radius is $R_{\rm c}\approx 66$ au |
| IM Lup disc mass (EDDY Gaussian) | 0.096 | not stated | M_sun | 4 | For EDDY , the best fit stellar mass is $M_\star\approx 1.02 \, \mathrm{M}_{\ensuremath{\odot}}$, the best fit disc mass is $M_{\rm d}\approx 0.096 \, \mathrm{M}_{\odot}$ and the scale radius is $R_{\rm c}\approx 66$ au |
| IM Lup scale radius Rc (EDDY Gaussian) | 66 | not stated | au | 4 | For EDDY , the best fit stellar mass is $M_\star\approx 1.02 \, \mathrm{M}_{\ensuremath{\odot}}$, the best fit disc mass is $M_{\rm d}\approx 0.096 \, \mathrm{M}_{\odot}$ and the scale radius is $R_{\rm c}\approx 66$ au |
| IM Lup stellar mass (DISCMINER Gaussian) | 1.01 | not stated | M_sun | 4 | For DISCMINER , the best fit stellar mass is $M_\star\approx 1.01 \, \mathrm{M}_{\ensuremath{\odot}}$, the best fit disc mass is $M_{\rm d}\approx 0.11 \, \mathrm{M}_{\odot}$ and the scale radius is $R_{\rm c}\approx 67$ au |
| IM Lup disc mass (DISCMINER Gaussian) | 0.11 | not stated | M_sun | 4 | For DISCMINER , the best fit stellar mass is $M_\star\approx 1.01 \, \mathrm{M}_{\ensuremath{\odot}}$, the best fit disc mass is $M_{\rm d}\approx 0.11 \, \mathrm{M}_{\odot}$ and the scale radius is $R_{\rm c}\approx 67$ au |
| IM Lup scale radius Rc (DISCMINER Gaussian) | 67 | not stated | au | 4 | For DISCMINER , the best fit stellar mass is $M_\star\approx 1.01 \, \mathrm{M}_{\ensuremath{\odot}}$, the best fit disc mass is $M_{\rm d}\approx 0.11 \, \mathrm{M}_{\odot}$ and the scale radius is $R_{\rm c}\approx 67$ au |
| IM Lup consistent disc mass | 0.1 | factor ~ 2 systematic | M_sun | 4 | For IM Lup, we are able to obtain a consistent disc mass of $M_{\rm disc}=0.1 \, \mathrm{M}_{\odot}$, implying a disc-star mass ratio of 0.1 (consistent with the observed spiral structure in the continuum emission) and a gas/dust ratio of $\sim 65$ (consistent with standard assumptions), with a systematic uncertainty by a factor $\simeq2$ due to the different methods to extract the rotation curve. |
| IM Lup disc-to-star mass ratio | 0.1 | not stated | dimensionless | 4 | For IM Lup, we are able to obtain a consistent disc mass of $M_{\rm disc}=0.1 \, \mathrm{M}_{\odot}$, implying a disc-star mass ratio of 0.1 (consistent with the observed spiral structure in the continuum emission) |
| IM Lup gas-to-dust ratio | 60 | not stated | dimensionless | 4 | Note that, given the known value of the dust mass of $M_{\rm dust}=1.7~10^{-3}\, \mathrm{M}_{\ensuremath{\odot}}$ (cite: Cleeves16), our measurement implies a gas/dust ratio of $\sim 60$, close to the standard assumed value of 100.; and a gas/dust ratio of $\sim 65$ (consistent with standard assumptions) |
| IM Lup Toomre Q in outer disc | 1 | not stated | dimensionless | 4 | In the outer disc, our model predicts $Q\sim 1$ indicating that the disc might be marginally gravitationally unstable, consistent with the observed large scale spiral structure in the dust morphology (cite: Huang18). |
| IM Lup stellar mass (EDDY Quadratic) | 1.03 | not stated | M_sun | 4 | Indeed, using the SHO quadratic method with EDDY , we obtain $M_\star \approx 1.03 \, \text{M}_\odot$, $M_\text{d} \approx 0.19 \, \text{M}_\odot$ and $R_\text{c} \approx 87 \, \text{au}$ |
| IM Lup disc mass (EDDY Quadratic) | 0.19 | not stated | M_sun | 4 | Indeed, using the SHO quadratic method with EDDY , we obtain $M_\star \approx 1.03 \, \text{M}_\odot$, $M_\text{d} \approx 0.19 \, \text{M}_\odot$ and $R_\text{c} \approx 87 \, \text{au}$ |
| IM Lup scale radius Rc (EDDY Quadratic) | 87 | not stated | au | 4 | Indeed, using the SHO quadratic method with EDDY , we obtain $M_\star \approx 1.03 \, \text{M}_\odot$, $M_\text{d} \approx 0.19 \, \text{M}_\odot$ and $R_\text{c} \approx 87 \, \text{au}$ |
| IM Lup stellar mass (DISCMINER Quadratic) | 1.02 | not stated | M_sun | 4 | while for DISCMINER quadratic we obtain again very good agreement for the disc and stellar masses ($M_\star \approx 1.02 \, \text{M}_\odot$, $M_\text{d} \approx 0.23 \, \text{M}_\odot$), but we were not able to fit for the disc scale radius. |
| IM Lup disc mass (DISCMINER Quadratic) | 0.23 | not stated | M_sun | 4 | while for DISCMINER quadratic we obtain again very good agreement for the disc and stellar masses ($M_\star \approx 1.02 \, \text{M}_\odot$, $M_\text{d} \approx 0.23 \, \text{M}_\odot$), but we were not able to fit for the disc scale radius. |
| GM Aur simultaneous fit disc mass (DISCMINER) | 0.26 | not stated | M_sun | 4 | The disc mass is $M_{\rm d}\approx 0.26\, \mathrm{M}_{\odot}$, the stellar mass is $M_{\star}\approx 0.7\, \mathrm{M}_{\odot}$ and the scale radius is $R_{\rm c}\approx 60$ au. |
| GM Aur simultaneous fit stellar mass (DISCMINER) | 0.7 | not stated | M_sun | 4 | The disc mass is $M_{\rm d}\approx 0.26\, \mathrm{M}_{\odot}$, the stellar mass is $M_{\star}\approx 0.7\, \mathrm{M}_{\odot}$ and the scale radius is $R_{\rm c}\approx 60$ au. |
| GM Aur simultaneous fit scale radius Rc (DISCMINER) | 60 | not stated | au | 4 | The disc mass is $M_{\rm d}\approx 0.26\, \mathrm{M}_{\odot}$, the stellar mass is $M_{\star}\approx 0.7\, \mathrm{M}_{\odot}$ and the scale radius is $R_{\rm c}\approx 60$ au. |
| GM Aur disc-to-star mass ratio | 0.35 | not stated | dimensionless | 4 | Our best fit disc mass measurement is $M_{\rm disc}=0.26 \, \mathrm{M}_{\odot}$, implying a disc-star mass ratio of $\sim 0.35$ and a gas/dust ratio of $\sim 130$. |
| GM Aur gas-to-dust ratio | 130 | not stated | dimensionless | 4 | Our best fit disc mass measurement is $M_{\rm disc}=0.26 \, \mathrm{M}_{\odot}$, implying a disc-star mass ratio of $\sim 0.35$ and a gas/dust ratio of $\sim 130$. |
| GM Aur individual 12CO fit stellar mass | 0.79 | not stated | M_sun | 4 | The resulting values for the star mass, disc mass and scale radius are: $M_{\star}\approx 0.79\, \mathrm{M}_{\odot}$, $M_{\rm d}\approx 0.11\, \mathrm{M}_{\odot}$ and $R_{\rm c}\approx 65$ au for the $^{12}$CO line fit |
| GM Aur individual 12CO fit disc mass | 0.11 | not stated | M_sun | 4 | The resulting values for the star mass, disc mass and scale radius are: $M_{\star}\approx 0.79\, \mathrm{M}_{\odot}$, $M_{\rm d}\approx 0.11\, \mathrm{M}_{\odot}$ and $R_{\rm c}\approx 65$ au for the $^{12}$CO line fit |
| GM Aur individual 12CO fit scale radius Rc | 65 | not stated | au | 4 | The resulting values for the star mass, disc mass and scale radius are: $M_{\star}\approx 0.79\, \mathrm{M}_{\odot}$, $M_{\rm d}\approx 0.11\, \mathrm{M}_{\odot}$ and $R_{\rm c}\approx 65$ au for the $^{12}$CO line fit |
| GM Aur second individual CO line fit stellar mass | 0.6 | not stated | M_sun | 4 | and a rather implausible $M_{\star}\approx 0.6\, \mathrm{M}_{\odot}$, $M_{\rm d}\approx 0.44\, \mathrm{M}_{\odot}$ and $R_{\rm c}\approx 59$ au for the $^{12}$CO line. |
| GM Aur second individual CO line fit disc mass | 0.44 | not stated | M_sun | 4 | and a rather implausible $M_{\star}\approx 0.6\, \mathrm{M}_{\odot}$, $M_{\rm d}\approx 0.44\, \mathrm{M}_{\odot}$ and $R_{\rm c}\approx 59$ au for the $^{12}$CO line. |
| GM Aur second individual CO line fit scale radius Rc | 59 | not stated | au | 4 | and a rather implausible $M_{\star}\approx 0.6\, \mathrm{M}_{\odot}$, $M_{\rm d}\approx 0.44\, \mathrm{M}_{\odot}$ and $R_{\rm c}\approx 59$ au for the $^{12}$CO line. |

## Qualitative findings

- For IM Lup, EDDY and DISCMINER yield consistent rotation curves and dynamical disc masses (~0.1 M_sun), implying a marginally gravitationally unstable outer disc (Q ~ 1) consistent with the observed dust spiral.  
  > "For this source, we obtain reliable rotation curves both with DISCMINER and EDDY and the two curves are consistent with each other. We fit the stellar mass to $M_\star \approx 1\, \mathrm{M}_{\odot}$, the disc mass to $M_{\rm d} \approx 0.1\, \mathrm{M}_{\odot}$" (Conclusions); "we estimate the gravitational stability parameter $Q$ to become $\sim 1$ in the outer disc, which points to a gravitational instability as the origin of the spiral structure observed in the dust morphology (cite: Huang18)." (Conclusions)
- Using the quadratic line centroid method rather than the Gaussian method increases the fitted disc mass of IM Lup by roughly a factor of 2.  
  > "In general, using the quadratic fit to the velocity results in a higher estimated disc mass, by roughly a factor 2." (Using the quadratic method to retrieve the rotation curves)
- For GM Aur, EDDY fails to retrieve an accurate rotation curve due to back-side emission contamination, and the DISCMINER rotation curves for 12CO and 13CO show a systematic offset that cannot be explained by emitting height differences or vertical temperature stratification.  
  > "Contamination from emission from the back side of the disc is particularly evident in this source and prevents EDDY from retrieving accurately the rotation curve." (Conclusions); "Additionally, the curves referring to the two isotopologues considered appear not to be consistent with each other, a difference that cannot be attributed by the difference in emitting scale height nor to a vertical temperature stratification." (Conclusions)

## Claim tuples

- H: Total protoplanetary disc mass and scale radius can be measured dynamically from high-resolution CO rotation curves by modeling self-gravity, radial pressure gradients, and emitting layer height. | E: Extract 12CO (2-1) and 13CO (2-1) rotation curves of IM Lup from MAPS data using both EDDY and DISCMINER and fit them simultaneously with an MCMC dynamical model. | R: Best-fit stellar mass M_* ~ 1.01-1.02 M_sun, disc mass M_d ~ 0.096-0.11 M_sun (Gaussian centroid), scale radius R_c ~ 66-67 au, and gas-to-dust ratio ~ 60-65. | F: A consistent dynamical disc mass of 0.1 M_sun is obtained for IM Lup across both extraction tools, with a factor ~2 systematic uncertainty between Gaussian and Quadratic centroid methods. | **supported**
- H: The large-scale dust spiral morphology in IM Lup can be driven by gravitational instability if the disc is sufficiently massive. | E: Compute the radial profile of the Toomre stability parameter Q from the best-fit dynamical surface density and scale height model of IM Lup. | R: In the outer disc, the best-fit dynamical model predicts Q ~ 1 and a disc-to-star mass ratio of ~ 0.1. | F: The outer disc of IM Lup is marginally gravitationally unstable, supporting gravitational instability as a viable origin for the observed spiral structure and kinematic wiggles. | **supported**
- H: The dynamical rotation curve fitting method can similarly constrain the disc mass of GM Aur using its 12CO and 13CO MAPS observations. | E: Extract 12CO and 13CO rotation curves of GM Aur with EDDY and DISCMINER, fit the DISCMINER curves simultaneously and individually, and test whether vertical temperature stratification explains the velocity offset between the two lines. | R: Simultaneous DISCMINER fit gives M_d ~ 0.26 M_sun, M_* ~ 0.7 M_sun, R_c ~ 60 au, but 12CO rotation velocities are systematically lower than 13CO by an amount an order of magnitude larger than predicted by vertical temperature stratification. | F: GM Aur's dynamical mass fit (0.26 M_sun) must be treated with caution because backside contamination, possible misestimation of emitting heights, or environmental perturbation from an infalling cloud prevent a consistent joint fit of the two CO isotopologues. | **partially**

## Reasoning

- Why this data: IM Lup and GM Aur have tentative evidence for high disc masses and exquisite high-spatial- and high-spectral-resolution kinematical data for both 12CO and 13CO from the ALMA MAPS Large Program.  
  > "In order to test our method to fit for the disc mass, based on the rotation curve, we have chosen two sources for which there is tentative evidence of a relatively massive disc, IM Lup and GM Aur for which high quality kinematical data are available from the MAPS survey (cite: Oberg21)." (Sample and data)
- Why this method: Fixing geometric and thermal/emitting-height parameters from literature avoids large parameter degeneracies while using both EDDY and DISCMINER tests robustness against systematic errors and lower-surface contamination.  
  > "Rather than constructing a single fitting procedure to fit for all of the unknown parameters (which would typically imply a large degree of degeneracy if the dataset is limited), here we assume some of the system parameters from the literature (e.g., geometry, height of the emitting layers,...) and fit for the stellar and disc masses based on an observed rotation curve." (Basic system parameters); "To test the robustness of our model we obtained the rotation curves of the two sources using both EDDY (cite: teague2019eddy) and DISCMINER (cite: Izquierdo21), each of which has got its advantages and drawbacks." (Extracting the rotation curve)
- Alternative: Simultaneously fitting all geometrical, physical, and radiative parameters in a single procedure was rejected because it would introduce large degeneracies.  
  > "Rather than constructing a single fitting procedure to fit for all of the unknown parameters (which would typically imply a large degree of degeneracy if the dataset is limited), here we assume some of the system parameters from the literature" (Basic system parameters)
- Alternative: Using a self-gravitating hyperbolic cosecant vertical density profile was rejected in favor of a vertically isothermal Gaussian-like profile because the star dominates the potential and the correction is higher order.  
  > "It is well known that for a self-gravitating disc the vertical structure is described by an hyperbolic cosecant function, with thickness given by (cite: KratterLodato)" (Disc radial and vertical structure); "This provides only a higher order correction to the rotation curve and we thus neglect it here." (Disc radial and vertical structure)
- Alternative: Using EDDY rotation curves for GM Aur was rejected due to severe contamination from the back side of the disc.  
  > "for the more challenging case of GM Aur, the contamination from the back side does not allow to use EDDY and for this source we only use the DISCMINER rotation curves." (Rotation curves: results)
- Alternative: Fitting a double Gaussian profile to the emission line to account for both upper and lower disc surfaces was noted as a possible improvement but not implemented.  
  > "A possible way to prevent this issue would be to fit with a double gaussian profile, in order to take into account both surfaces but we have not implemented it in this work." (Using the quadratic method to retrieve the rotation curves)
- How they decided it was enough: _not stated_
- Limitation (authors): Measurement points of the rotation curve are treated as independent in the MCMC fit, neglecting covariance and underestimating statistical parameter uncertainties.  
  > "Note that in the fitting procedure we have neglected the fact that the measurement points of the rotation curve are not fully independent. This has an impact on the estimated parameter uncertainty (here and for all the other fits presented below), which is in fact an underestimate." (IM Lup)
- Limitation (authors): The rotation curve model assumes vertical isothermality and does not include vertical temperature stratification in the dynamical fit.  
  > "One additional refinement to the model (not included in the present work) is to also include vertical temperature stratification in the modeling of the rotation curve, that we defer to subsequent work." (Conclusions)
- Limitation (authors): The model uses azimuthally averaged rotation curves and does not model non-axisymmetric kinematic perturbations (such as spirals or planet wakes).  
  > "Firstly, we explicitly note that our model employs the azimuthally averaged rotation curve and we thus do not model in any way possible non-axisymmetric deviations from Keplerianity" (Non axi-symmetric kinematics and spiral structure in IM Lup)
- Limitation (authors): Outer disc kinematics in GM Aur are perturbed by interaction with an infalling cloud, so CO velocities may not trace pure centrifugal balance.  
  > "We know that the outer disc of GM Aur is highly perturbed (cite: Schwarz21) and the gas kinematics might thus not trace pure rotational motions. Thus, our results for the GM Aur disc should be regarded with some caution." (GM Aur)
- Limitation (authors): Geometrical and emitting-height parameters are fixed from literature values rather than jointly fitted, so systematic errors in z(R) propagate into the extracted rotation curves.  
  > "Indeed, the height of the emitting layer $z(R)$ affects the retrieval of the rotation curve." (Conclusions); "In the present work, we have simply assumed these parameters from the literature, but in the future one might want to construct a single framework to simultaneously fit the whole disc kinematical structure." (Conclusions)
- Caveat (inferred, ours): In Section 4.2 (GM Aur), there is a typo where both individual line fits are labeled 'for the 12CO line' ('M_* approx 0.79 M_sun... for the 12CO line fit and a rather implausible M_* approx 0.6 M_sun... for the 12CO line'), though context and Fig. 5 caption indicate the second set of numbers corresponds to 13CO.
- Caveat (inferred, ours): Section 3.3.1 states that 'inclination and position angle, see Table 1' are used, but Table 1 only lists inclination i and omits position angle PA.
- Caveat (inferred, ours): Statistical error bars on fitted parameters are not reported in the main text (only approximate best-fit values are given in prose, with posteriors shown graphically in corner plots).

## Reproducibility

- Data public (paper): Publicly available from the MAPS survey website (https://alma-maps.info/data.html) and ALMA archive (2018.1.01055.L).  
  > "The kinematical data of the CO molecules used in this paper are publiclly avaiable from the MAPS survey <https://alma-maps.info/data.html>." (Data Availability); "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2018.1.01055.L." (Acknowledgements)
- Products in archive: Delivered spectral-line cubes from the MAPS survey are available online.  
  > "“For the delivered data products the velocity resolutions have been coarsened to achieve more uniformity between spectral-line cubes as described in (cite: Czekala21)”" (IM Lup); "The kinematical data of the CO molecules used in this paper are publiclly avaiable from the MAPS survey <https://alma-maps.info/data.html>." (Data Availability)
- Code: MCMC dynamical rotation curve fitting code 'DySc - Dynamical Scale' is publicly available on GitHub at https://github.com/crislong/DySc.  
  > "The MCMC fitting procedure code we used is publicly available on GitHub “DySc - Dynamical Scale" [^3]" (Results); "[^3]: <https://github.com/crislong/DySc>." (GM Aur)
- Missing: Exact Position Angle (PA) values adopted for IM Lup and GM Aur (must be looked up in Oberg et al. 2021 / Law et al. 2021)
- Missing: Which specific MAPS cube variant (e.g., robust 0.5 vs circularized beam, JvM-corrected vs residual-scaled) was used as input to EDDY and DISCMINER
- Missing: Radial bin spacing and exact inner/outer radius values in au used in the rotation curve extraction
- Missing: Exact likelihood weighting / error bar definition on the extracted rotation curve points passed into emcee
- Data volume (inferred): A few GB (4 high-resolution spectral line cubes from MAPS for 2 targets in 12CO and 13CO 2-1)
- Score (inferred): 9/5, The input spectral cubes are publicly hosted by the MAPS survey, the extraction tools (EDDY and DISCMINER) are public, the authors released their MCMC dynamical fitting code (DySc) on GitHub, and almost all fixed structural parameters, equations, and MCMC settings/priors are explicitly tabulated.
- Rediscovery candidate: yes, Public MAPS data cubes, public analysis and fitting codes (EDDY, DISCMINER, DySc), well-defined analytical/numerical equations, and clear numeric target quantities (stellar mass, disc mass, scale radius).

## Links

- Method: (cite: Veronesi21) (Introduced the dynamical disc mass measurement method using self-gravitating rotation curves (applied to Elias 2-27).)
- Method: (cite: teague2019eddy); (cite: teague2018kinematical); (cite: teague2018evidence); (cite: teague2018robust) (Describe the EDDY package, the Simple Harmonic Oscillator (SHO) rotation curve retrieval method, and Gaussian/Quadratic line centroid fitting.)
- Method: (cite: Izquierdo21) (Introduces the DISCMINER package used to extract rotation curves and mask contamination from the lower emitting surface.)
- Method: (cite: BL99) (Provides the elliptic integral formulation for the gravitational potential contribution of an axisymmetric thin disc.)
- Companion: (cite: Oberg21) (Overview paper of the ALMA MAPS Large Program providing the archival data and basic geometric parameters.)
- Companion: (cite: Law21) (MAPS companion paper providing the 12CO and 13CO emitting surface heights and 2D temperature profiles used in the analysis.)
- Companion: (cite: Zhang21) (MAPS companion paper providing the thermochemical model parameters for the pressure scale height H0 and q.)
- Companion: (cite: Schwarz21); (cite: Huang21); (cite: Czekala21) (MAPS companion papers describing GM Aur's thermochemical structure, extended outer disc/spiral environment, and spectral-line imaging products.)
- Related: MAPS (Molecules with ALMA at Planet-forming Scales)

## Checks

```json
{
 "quotes": 139,
 "quotes_ok": 139,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 12,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 26,
 "numeric_problems": 0,
 "fill": {
  "facts": 97,
  "stated": 63,
  "rate": 0.649
 },
 "evidence_ok": true
}
```
