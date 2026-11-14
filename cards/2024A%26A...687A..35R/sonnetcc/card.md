# Dynamical modelling and the origin of gas turbulence in z ∼ 4.5 galaxies

`2024A&A...687A..35R` | Astronomy and Astrophysics 2024 | first author: Roman-Oliveira, F. | arXiv: 2403.00904 | DOI: 10.1051/0004-6361/202348828

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type archival_reuse

## Science

- Fields: high_z_galaxies
- Question: Derive the structural properties of the gas, stars and dark matter halos of four z ~ 4.5 [CII] discs via rotation-curve mass decomposition, and test whether stellar feedback or gravitational instabilities drive their turbulence  
  > "We aim to derive the structural properties of the gas, stars and dark matter halos of the galaxies" (abstract); "Furthermore, we use the gas velocity dispersion profiles as a diagnostic tool for the mechanisms driving the turbulence in the discs." (abstract)
- Target **BRI1335-0417**: coordinates _not stated_; z/distance z ~ 4.5 (sample)  
  > "one of the galaxies is a quasar host (BRI1335-0417), two are in a group (SGP38326-1 and SGP38326-2)" (2 Data and methods); distance from _not stated_
- Target **J081740**: coordinates _not stated_; z/distance z ~ 4.5 (sample)  
  > "the remaining galaxy was originally discovered as a damped Lyman alpha system" (2 Data and methods); distance from _not stated_
- Target **SGP38326-1**: coordinates _not stated_; z/distance z ~ 4.5 (sample)  
  > "two are in a group (SGP38326-1 and SGP38326-2)" (2 Data and methods); distance from _not stated_
- Target **SGP38326-2**: coordinates _not stated_; z/distance z ~ 4.5 (sample)  
  > "two are in a group (SGP38326-1 and SGP38326-2)" (2 Data and methods); distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.00330.S, 2017.1.00127.S, 2017.1.00394.S, 2017.1.01052.S, 2018.1.00001.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.13" - 0.24" (6 - 10 independent radial elements across the major axis)  
  > "spatial resolutions in the range of 0.13" - 0.24", which correspond to 6 - 10 independent radial elements across the major axis of the galaxies" (2.4 Gas kinematics)
- max recoverable scale: _not stated_
- sensitivity: average SNR of 3 - 5 per pixel and velocity channel  
  > "These observations have an average SNR of 3 - 5 per pixel and velocity channel" (2.4 Gas kinematics)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: archival data selected from the ALMA archive for SNR, angular and spectral resolution  
  > "The galaxies in this sample were selected due to the quality of the data available in the ALMA archive, in terms of SNR, angular and spectral resolution." (2 Data and methods)
- Line: [CII] 158 um fine-structure line (not stated)
- Other facility **WISE**: data products used (role not specified in the text)  
  > "This publication makes use of data products from the Wide-field Infrared Survey Explorer" (Acknowledgements)
- External data: [CII] rotation curves and velocity dispersion profiles (3DBarolo) for the four galaxies  
  > "in addition to the kinematic profiles from (cite: romanoliveira23)" (2 Data and methods); "Here we use the kinematic profiles obtained in our previous paper" (2.4 Gas kinematics) [from (cite: romanoliveira23)]
- External data: CO luminosities (lowest CO transitions) used to scale the gas mass (Table 1)  
  > "we report the CO luminosities for the lowest CO transitions available in the literature for the galaxies in our sample" (2.1 Molecular gas mass) [from (cite: jones16); (cite: wagg14); (cite: neeleman20); (cite: oteo16); (cite: fudamoto17)]
- External data: SFRs of J081740, SGP38326-1 and SGP38326-2 from total IR luminosity  
  > "The global star formation rate (SFR) of the galaxies J081740, SGP38326-1 and SGP38326-2 were derived from the total IR luminosity" (2.2 Star Formation Rates) [from (cite: neeleman20); (cite: oteo16)]
- External data: SFR of BRI1335-0417 with AGN contribution to dust heating excluded  
  > "rederived the SFR by taking into account the spatially resolved nuclear emission and thus excluding the contribution of the AGN to the dust heating" (2.2 Star Formation Rates) [from (cite: tsukui23)]
- External data: Krumholz et al. analytical model of turbulence driven by gravitational instabilities or stellar feedback, with fiducial high-z parameters  
  > "we compare the observed gas velocity dispersions to those expected by the analytical model from (cite: krumholz18)" (3.4.1 Gravitational Instabilities) [from (cite: krumholz18)]
- External data: NFW concentration of 3.4 taken as typical for z ~ 4.5 CDM halos  
  > "which is the typical value of concentration for a wide range of CDM halo masses at" (2.6 Mass Decomposition) [from (cite: dutton14); (cite: correa15); (cite: child18)]
- External data: Main-sequence relation at z = 4.5 for the SFR vs stellar mass comparison  
  > "compared to the main-sequence relation at" (3.3 Star Formation Rates and Stellar Masses) [from (cite: speagle14)]
- External data: Local ETG analogue Tully-Fisher data and best-fit relation (MASSIVE survey, revised inclinations)  
  > "we compare our sample to local ETGs, both elliptical and lenticular galaxies, from the MASSIVE survey (cite: ma14)" (4.2.1 Tully-Fisher relations) [from (cite: ma14); (cite: davis16); (cite: fraternali21)]
- External data: Abundance-matching SHMR at 4.5 < z < 5.5  
  > "We compare this to the expected relation from abundance-matching techniques at" (4.2.2 The Stellar-to-Halo Mass Relation) [from (cite: shuntov22)]

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
- continuum subtraction: line emission separated from continuum to make a dust-continuum image and a [CII] datacube (details deferred to Roman-Oliveira et al. 2023)  
  > "First, we separate the line-emission from the continuum and produce a dust-continuum only image" (2.3 Dust and gas surface profiles)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Sersic models convolved to the same resolution as the data when fitting  
  > "To account for the spatial resolution of the data, we convolve the model to the same resolution as the data." (2.3 Dust and gas surface profiles)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- ALMA data reduction and imaging  
  > "For more details on the ALMA data reduction and imaging refer to (cite: romanoliveira23)." (2.3 Dust and gas surface profiles) [from (cite: romanoliveira23)]
- Kinematic modelling details and the rotation curve / velocity dispersion profiles used  
  > "For more details we refer to (cite: romanoliveira23)." (2.4 Gas kinematics) [from (cite: romanoliveira23)]
- Residual-asymmetry effective uncertainty used as sigma in the Sersic chi-square fit  
  > "based on the methodology employed by (cite: marasco19), we rotate the moment 0 map of the emission by" (2.3 Dust and gas surface profiles) [from (cite: marasco19)]
- Density-potential relation for the stellar circular speed from a deprojected spherical Sersic profile  
  > "We use a density–potential relation for a deprojected spherical Sérsic profile from (cite: terzic05)" (2.6 Mass Decomposition) [from (cite: terzic05)]
- Supernova-driven turbulence energy model  
  > "we use a simple model in which we assume that the turbulence of the gas is fed by the energy injected in the ISM by supernova explosions (cite: bacchini20)" (2.7 Supernova explosion driven turbulence) [from (cite: bacchini20)]
- Disc inclination of 42 deg for BRI1335-0417  
  > "Considering the disc inclination of 42$^{\circ}$ as derived in (cite: romanoliveira23)" (8 Dynamical Models) [from (cite: romanoliveira23)]

### Not stated but needed to reproduce (our reading)

- ALMA band, frequencies, spectral setup, array configurations, baselines, time on source and observing dates for each project are not given; they are in the earlier paper
- Which ALMA project code belongs to which galaxy
- CASA version, tclean parameters (weighting, robust, cell, image size, masking, line-free channels), and any self-calibration are deferred to Roman-Oliveira et al. 2023
- Exact [CII] integration channel range for the moment-0 maps
- Position-dependent sigma_eff values and DYNESTY settings (live points, stopping criterion, nested-sampling mode) for both the Sersic and mass-decomposition fits
- Likelihood form used for the rotation-curve decomposition (not given), and how the asymmetric-drift-corrected circular speed uncertainties enter it
- Which of the surface-brightness table rows belong to which galaxy (rows are unlabelled in the text)
- Exact SFRs used for BRI1335-0417 (1700 +500/-400 is given) and the h, eta, and xi values per galaxy in Figure 6
- Rest frequency of [CII] and redshifts of the individual galaxies
- Prior probability treatment of the 3-sigma/asymmetric uncertainties and how the quoted best-fit values are summarised (median vs maximum)

## Analysis recipe

1. **make dust-continuum image and [CII] moment-0 map**: separate line from continuum, make a dust-continuum image and a [CII] datacube, integrate cube along velocity for the [CII] total emission map  
  > "First, we separate the line-emission from the continuum and produce a dust-continuum only image" (2.3 Dust and gas surface profiles); "With the datacube, we obtain the" (2.3 Dust and gas surface profiles)
   - software: CASA
   - assumption: [CII] emission traces the total gas distribution, so gas surface density is proportional to [CII] surface brightness  
  > "the gas surface density is proportional to the" (2.3 Dust and gas surface profiles)
   - fitting: _not stated_
   - validation: _not stated_
2. **fit 2D Sersic profiles to [CII] and dust maps**: 2D Sersic fit with model convolved to data resolution, DYNESTY sampling  
  > "To account for the spatial resolution of the data, we convolve the model to the same resolution as the data." (2.3 Dust and gas surface profiles); "We then minimise the residuals to find the best-fit model using" (2.3 Dust and gas surface profiles)
   - software: Astropy, DYNESTY
   - parameter: free: R_eff, I_e, centre (x0, y0), ellipticity, PA, for both gas and dust  
  > "For both the gas and the dust we leave all the following parameters free:" (2.3 Dust and gas surface profiles)
   - parameter: uniform priors  
  > "to compute the Bayesian posterior distribution of these parameters considering uniform priors." (2.3 Dust and gas surface profiles)
   - parameter: Sersic index fixed to 1 for all fits except BRI1335-0417 dust (free); a preliminary free-n fit varied n within 0.2 and 10.0  
  > "we perform a preliminary fit letting" (2.3 Dust and gas surface profiles); "we prefer to fix it to 1 in our fits for all galaxies, with the only exception of the dust emission of BRI for which we leave" (2.3 Dust and gas surface profiles)
   - parameter: SGP38326-1 and -2 fitted simultaneously; small companion SGP38326-3 masked  
  > "we also masked the emission of the small companion (SGP38326-3)" (3.1 Surface Brightness)
   - parameter: sigma = standard deviation of residual map after subtracting the moment 0 map rotated by 180 deg  
  > "We then calculate the standard deviation of this residual map" (2.3 Dust and gas surface profiles)
   - assumption: discs razor-thin, inclination from ellipticity (cos^2 i = 1 - eps)  
  > "Finally, we assume the discs to be razor-thin such that the inclination is related to the ellipticity by" (2.3 Dust and gas surface profiles)
   - assumption: gas disc scale length R_gas = R_eff,[CII]/1.678 for an exponential profile  
  > "After deriving the \[CII\] surface brightness profiles as an exponential profile" (2.3 Dust and gas surface profiles)
   - fitting: DYNESTY dynamic nested sampling, uniform priors, chi-square likelihood weighted by an effective uncertainty from the asymmetry of the galaxy  
  > "In the fitting, we minimise the residuals using a chi-square likelihood," (2.3 Dust and gas surface profiles); "we weight the residuals by an effective uncertainty related to asymmetry in the galaxy (cite: marasco19)" (2.3 Dust and gas surface profiles)
   - validation: maps well reproduced with minimal residuals; outer-region surface brightness slightly overestimated; only R_eff is used downstream  
  > "the maps are well reproduced with minimal residuals." (2.3 Dust and gas surface profiles); "Given that we only use the effective radii of these fits in the following analysis" (3.1 Surface Brightness)
3. **adopt rotation curves and dispersion profiles**: use 3DBarolo kinematic profiles (rotation curves and velocity dispersion) from the previous paper  
  > "Here we use the kinematic profiles obtained in our previous paper, namely the rotation curves to perform the dynamical modelling and the velocity dispersion profiles to study the turbulence in the discs." (2.4 Gas kinematics)
   - software: 3DBarolo
   - assumption: axisymmetric rotating disc model  
  > "which fits the full emission line datacube considering an axisymmetric rotating disc model." (2.4 Gas kinematics)
   - fitting: _not stated_
   - validation: _not stated_
4. **correct rotation curves for pressure support**: asymmetric drift correction assuming an exponential gas disc with the best-fit [CII] scale length, numerically differentiating ln sigma  
  > "we assume that the gas is distributed as an exponential disc and use the best-fit disc scale length reported in" (6 Asymmetric Drift Correction)
   - assumption: isotropic velocity ellipsoid and disc thickness constant with radius  
  > "Assuming that the velocity ellipsoid is isotropic and the disc thickness is constant with radius" (2.5 Circular speed of the gas)
   - fitting: _not stated_
   - validation: for BRI1335-0417 the result agrees with the circular speed derived with 3DBarolo  
  > "in spite of the difference in methodology, agrees with the circular speed derived with" (6 Asymmetric Drift Correction)
5. **decompose circular speed into stars, gas and DM**: fit V_c(R) = sqrt(V_star^2 + V_gas^2 + V_DM^2) with Sersic-stellar (Terzic and Graham density-potential), razor-thin exponential gas disc and NFW halo components  
  > "to reproduce the observed circular speed of the galaxy using" (2.6 Mass Decomposition); "We use a density–potential relation for a deprojected spherical Sérsic profile from (cite: terzic05)" (2.6 Mass Decomposition)
   - software: DYNESTY
   - parameter: log M* uniform 9 - 12; stellar Sersic n uniform 0.2 - 10; R_eff,* uniform between R_eff of dust and of [CII]  
  > "We let the log of the stellar mass vary uniformly between 9 and 12." (2.6 Mass Decomposition); "The Sérsic index is free to vary uniformly between 0.2 and 10." (2.6 Mass Decomposition); "Lastly, the effective radius is free to vary uniformly between the effective radius of the dust and that of the" (2.6 Mass Decomposition)
   - parameter: M_gas = L_CO x gas_norm, with gas_norm uniform 0 - 10  
  > "We use a uniform prior ranging from 0 to 10, where the former represents the complete lack of gas in the galaxy" (2.6 Mass Decomposition)
   - parameter: NFW concentration fixed at 3.4; baryon fraction uniform in log between 1e-6 and 0.187 (log f_bar -6 to -0.73)  
  > "We let the baryon fraction, $f_{\mathrm{bar}}$, vary uniformly in a log space." (2.6 Mass Decomposition); "We let $f_{\mathrm{bar}}$ vary between the cosmological baryon fraction of 0.187 (cite: planck20) and a baryon fraction of 10$^{-6}$" (2.6 Mass Decomposition)
   - parameter: BRI1335-0417: baryon fraction fixed to the cosmological value in the fiducial model  
  > "for the galaxy BRI1335-0417, a different approach was taken, wherein the baryon fraction was fixed to the cosmological baryon fraction" (3.2 Mass decomposition of the rotation curves)
   - assumption: gas follows an exponential razor-thin disc with the [CII] scale length  
  > "we assume this component to be a razor-thin disc following an exponential disc profile" (2.6 Mass Decomposition)
   - assumption: spherical NFW halo  
  > "we assume this component to be a spherical NFW halo profile (cite: navarro97)" (2.6 Mass Decomposition)
   - assumption: stellar component spherical with Sersic light profile  
  > "we assume that the projected light distribution follows a Sérsic profile." (2.6 Mass Decomposition)
   - fitting: DYNESTY Bayesian posterior over M*, R_eff,*, n, gas_norm, f_bar (four free for BRI1335-0417); likelihood not stated  
  > "We compute Bayesian posterior distribution of the following free parameters:" (2.6 Mass Decomposition)
   - validation: tests with a larger stellar-radius prior did not change other parameters; oversampled rotation curves gave no significant change; free-inclination and free-concentration tests for BRI1335-0417  
  > "We find that it does not impact the estimates of the other parameters significantly" (2.6 Mass Decomposition); "we find that neither retrieve significantly different results" (8 Dynamical Models)
6. **derive gas fraction, baryonic radius and disc fraction**: compute f_gas = M_gas/M_bar, effective baryonic radius (half baryonic mass) and disc fraction (baryons to DM inside that radius) from the decomposition; place galaxies on SFR vs M* plane  
  > "the baryonic effective radius, defined as the radius that comprises half of the baryonic mass" (3.2 Mass decomposition of the rotation curves); "we show the position of our galaxies in the SFR vs stellar mass plane" (3.3 Star Formation Rates and Stellar Masses)
   - assumption: SFRs from IR luminosity converted to a Chabrier IMF; stellar masses from the decomposition  
  > "The SFRs are derived from IR luminosities and converted to a Chabrier IMF as described in Section" (3.3 Star Formation Rates and Stellar Masses)
   - fitting: _not stated_
   - validation: _not stated_
7. **compare dispersions with gravity- and feedback-driven turbulence models**: compare observed velocity dispersion vs SFR to the two Krumholz et al. scenarios (gravitational instability only; stellar feedback only) at circular speeds spanning the sample  
  > "we compare the observed gas velocity dispersions to those expected by the analytical model from (cite: krumholz18)" (3.4.1 Gravitational Instabilities); "In both scenarios we use the fiducial parameters for high-*z* galaxies as reported in (cite: krumholz18)" (3.4.1 Gravitational Instabilities)
   - assumption: Toomre Q marginally stable in both scenarios  
  > "Both assume that the Toomre Q parameter" (3.4.1 Gravitational Instabilities)
   - fitting: _not stated_
   - validation: stellar-feedback-only model reproduces the data trends much better than the gravity-only model  
  > "Instead, the stellar feedback only model is significantly better at reproducing the data trends" (3.4.1 Gravitational Instabilities)
8. **compare SNII energy input with observed turbulent energy**: E_SN = eta * E_SNII * xi * h / sigma compared with E_turb = 3/2 M_gas sigma^2; eta = 1 gives the maximum injectable energy, identity lines show eta  
  > "The turbulence due to the supernova energy input is dissipated with a timescale" (2.7 Supernova explosion driven turbulence); "where the x-axis shows the maximum injectable energy expected from SNII calculated with Equation" (3.4.2 Stellar Feedback)
   - parameter: E_SNII = 10^51 erg per SNII; xi = 0.01 per Msun x SFR for a Chabrier IMF  
  > "Assuming a Chabrier IMF, the rate of SNII is given by" (2.7 Supernova explosion driven turbulence)
   - parameter: thin disc h = 0.3 kpc and thick disc h = 1.0 kpc  
  > "Since we do not have reliable information about the thickness of gas discs, we analyse two different assumptions" (3.4.2 Stellar Feedback)
   - assumption: SNIa neglected as high-z galaxies are SNII dominated  
  > "Here, we neglect the contribution from supernova type Ia (SNIa)" (2.7 Supernova explosion driven turbulence)
   - assumption: line-of-sight dispersion isotropic; thermal broadening negligible  
  > "that we assume to be isotropic." (2.7 Supernova explosion driven turbulence)
   - fitting: _not stated_
   - validation: eta of order 10% or less is expected from hydrodynamical simulations of supernova remnants  
  > "We note that hydrodynamical simulations of supernova remnant evolution tend to find values of" (2.7 Supernova explosion driven turbulence)
9. **place galaxies on scaling relations**: compare with the local baryonic Tully-Fisher relation (external circular speed = mean of the outer two resolution-independent elements), the ETG analogue Tully-Fisher relation (stellar and baryonic mass), and the SHMR  
  > "we compare our sample to the BTFR for local disc galaxies" (4.2.1 Tully-Fisher relations); "the external circular speeds defined as the average of the circular speed from the outer two resolution independent elements" (4.2.1 Tully-Fisher relations)
   - assumption: for the ETG relation the gas is assumed fully converted into stars by z = 0 when adding gas to stellar mass  
  > "once we assume that their gas content will be fully converted into stars by" (4.2.1 Tully-Fisher relations)
   - fitting: _not stated_
   - validation: BRI1335-0417 plotted as open symbol because only an upper limit on the baryonic mass is available  
  > "we only have upper limits in the baryonic mass and therefore its placement in the BTFR is more uncertain" (4.2.1 Tully-Fisher relations)

## Software

- **CASA** : separate line from continuum and make dust-continuum image and [CII] cube (mfs and cube modes)  
  > "First, we separate the line-emission from the continuum and produce a dust-continuum only image" (2.3 Dust and gas surface profiles)
- **Astropy** : Sersic2D function for the 2D surface brightness model  
  > "which takes into account the geometric parameters defining the 2D distributions, the ellipticity $\epsilon$, the position angle (PA) and the centre." (2.3 Dust and gas surface profiles)
- **DYNESTY** : Bayesian posteriors for the Sersic fits and the mass decomposition  
  > "a python package for estimating Bayesian posteriors and evidences using the Dynamic Nested Sampling algorithm" (2.3 Dust and gas surface profiles)
- **3DBarolo** : kinematic modelling of the [CII] datacubes (done in the previous paper)  
  > "which fits the full emission line datacube considering an axisymmetric rotating disc model." (2.4 Gas kinematics)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| total stellar mass range of the four galaxies, log(M*/Msun) | 10.3 - 11.0 | not stated | dex (log Msun) | 5 | We obtain total stellar, gas and dark matter masses in the ranges of $\log{(M/M_{\odot})} = 10.3 - 11.0$, $9.8 - 11.3$, and $11.2 - 13.3$, respectively. |
| total gas mass range, log(Mgas/Msun) | 9.8 - 11.3 | not stated | dex (log Msun) | 5 | We obtain total stellar, gas and dark matter masses in the ranges of $\log{(M/M_{\odot})} = 10.3 - 11.0$, $9.8 - 11.3$, and $11.2 - 13.3$, respectively. |
| dark matter halo mass range, log(M200/Msun) | 11.2 - 13.3 | not stated | dex (log Msun) | 5 | We obtain total stellar, gas and dark matter masses in the ranges of $\log{(M/M_{\odot})} = 10.3 - 11.0$, $9.8 - 11.3$, and $11.2 - 13.3$, respectively. |
| baryon fraction range | 0.006 up to the cosmological value 0.187 | not stated | dimensionless | 5 | with baryon fractions of 0.006 up to the cosmological baryon fraction of 0.187. |
| BRI1335-0417 log M*, Reff,* (kpc), n, gas_norm, log Mgas, log M200 (fixed) | 10.4, 2.3, 6.9, 0.06, 9.8, 11.2 (fixed) | log M* +0.1/-0.1; Reff,* +0.5/-0.4; n +2.1/-2.1; gas_norm +0.06/-0.04; log Mgas +0.3/-0.5 | log Msun; kpc; dimensionless; dimensionless; log Msun; log Msun | 5 | / BRI1335-0417 / 10.4 $^{+0.1}_{-0.1}$ / 2.3 $^{+0.5}_{-0.4}$ / 6.9 $^{+2.1}_{-2.1}$ / 0.06 $^{+0.06}_{-0.04}$ / *-0.728* / 9.8 $^{+0.3}_{-0.5}$ / *11.2* / |
| J081740 log M*, Reff,* (kpc), n, gas_norm, log fbar, log Mgas, log M200 | 10.6, 2.4, 6.7, 1.4, -1.5, 10.5, 12.3 | +0.2/-0.2; +0.5/-0.5; +2.3/-2.4; +1.2/-0.9; +0.5/-0.7; +0.3/-0.5; +0.7/-0.5 | log Msun; kpc; dimensionless; dimensionless; dimensionless; log Msun; log Msun | 5 | / J081740 / 10.6 $^{+0.2}_{-0.2}$ / 2.4 $^{+0.5}_{-0.5}$ / 6.7 $^{+2.3}_{-2.4}$ / 1.4 $^{+1.2}_{-0.9}$ / -1.5 $^{+0.5}_{-0.7}$ / 10.5 $^{+0.3}_{-0.5}$ / 12.3 $^{+0.7}_{-0.5}$ / |
| SGP38326-1 log M*, Reff,* (kpc), n, gas_norm, log fbar, log Mgas, log M200 | 11.0, 2.2, 6.3, 1.9, -1.7, 11.3, 13.2 | +0.2/-0.2; +0.7/-0.6; +2.5/-2.4; +0.6/-0.9; +0.7/-0.9; +0.1/-0.3; +0.9/-0.7 | log Msun; kpc; dimensionless; dimensionless; dimensionless; log Msun; log Msun | 5 | / SGP38326-1 / 11.0 $^{+0.2}_{-0.2}$ / 2.2 $^{+0.7}_{-0.6}$ / 6.3 $^{+2.5}_{-2.4}$ / 1.9 $^{+0.6}_{-0.9}$ / -1.7 $^{+0.7}_{-0.9}$ / 11.3 $^{+0.1}_{-0.3}$ / 13.2 $^{+0.9}_{-0.7}$ / |
| SGP38326-2 log M*, Reff,* (kpc), n, gas_norm, log fbar, log Mgas, log M200 | 10.3, 1.7, 5.3, 2.5, -2.2, 11.1, 13.3 | +0.4/-0.6; +0.4/-0.4; +3.1/-2.9; +1.1/-1.4; +1.0/-1.3; +0.2/-0.3; +1.3/-1.0 | log Msun; kpc; dimensionless; dimensionless; dimensionless; log Msun; log Msun | 5 | / SGP38326-2 / 10.3 $^{+0.4}_{-0.6}$ / 1.7 $^{+0.4}_{-0.4}$ / 5.3 $^{+3.1}_{-2.9}$ / 2.5 $^{+1.1}_{-1.4}$ / -2.2 $^{+1.0}_{-1.3}$ / 11.1 $^{+0.2}_{-0.3}$ / 13.3 $^{+1.3}_{-1.0}$ / |
| BRI1335-0417 dust Sersic index | 2.6 | 0.1 | dimensionless | 2 | it is significantly better described by a Sérsic index of $n = 2.6 \pm 0.1$. |
| BRI1335-0417 gas fraction, Reff,bar (kpc), disc fraction | 0.16, 2.9, 0.69 | f_gas 0.12 | dimensionless; kpc; dimensionless | 6 | / BRI1335-0417 / 0.16 $\pm$ 0.12 / 2.9 / 0.69 / |
| J081740 gas fraction, Reff,bar (kpc), disc fraction | 0.52, 2.8, 0.63 | f_gas 0.24 | dimensionless; kpc; dimensionless | 6 | / J081740 / 0.52 $\pm$ 0.24 / 2.8 / 0.63 / |
| SGP38326-1 gas fraction, Reff,bar (kpc), disc fraction | 0.68, 2.8, 0.78 | f_gas 0.17 | dimensionless; kpc; dimensionless | 6 | / SGP38326-1 / 0.68 $\pm$ 0.17 / 2.8 / 0.78 / |
| SGP38326-2 gas fraction, Reff,bar (kpc), disc fraction | 0.87, 2.0, 0.72 | f_gas 0.22 | dimensionless; kpc; dimensionless | 6 | / SGP38326-2 / 0.87 $\pm$ 0.22 / 2.0 / 0.72 / |
| SNII kinetic efficiency eta: three galaxies / BRI1335-0417 | eta ~ 0.1 (three galaxies); eta ~ 0.001 - 0.01 (BRI1335-0417) | not stated | dimensionless | 8 | We find that the three of the galaxies are consistent with $\eta \approx 0.1$ while BRI1335-0417 is more consistent with a lower efficiency of $\eta \approx 0.001 - 0.01$. |
| BRI1335-0417 mass enclosed by innermost and outermost ring from circular speeds of 191 and 153 km/s | 4.2e9 (innermost); 2.5e10 (outermost) | not stated | Msun | 4 | we find that the innermost ring encloses a mass of $4.2 \times 10^9 M_\odot$ and the outermost ring encloses a mass of $2.5 \times 10^{10} M_\odot$. |
| BRI1335-0417 test with free DM concentration: stellar mass and c200 | M* = 2.4e10 Msun, c200 = 2.6 | not stated | Msun; dimensionless | 5 | we find a stellar mass of $2.4 \times 10^{10} M_\odot$, a concentration $c_{200}$ of 2.6 |

## Qualitative findings

- All four galaxies require a compact, massive stellar component (Sersic n > ~5, within ~2 kpc), compatible with a stellar bulge  
  > "there must be a massive compact stellar component dominating in the inner 2 kpc of the galaxies in our sample, compatible with what would be expected from a stellar bulge." (5 Conclusions)
- Gas turbulence is reproduced by stellar feedback alone without large-scale gravitational instabilities  
  > "the observed gas turbulence in the discs can be fully reproduced by the stellar feedback alone, without the need for large-scale gravitational instabilities or other mechanisms." (5 Conclusions)
- Galaxies are strongly baryon dominated in the inner 3 to 5 kpc, with gas-to-baryon fractions 0.16 to 0.87  
  > "We found that our galaxies are strongly baryon dominated in the regions probed (inner 3 to 5 kpc)" (5 Conclusions); "that they have a variety of gas-to-baryon fractions, from 0.16 to 0.87." (5 Conclusions)
- No significant deviation of the sample towards higher stellar fractions at the massive end of the SHMR  
  > "we do not find any significant deviation towards higher stellar fractions at the massive end." (4.2.2 The Stellar-to-Halo Mass Relation)

## Claim tuples

- H: Do z ~ 4.5 [CII] discs host compact stellar components? | E: Decompose the circular speeds into stars, gas and NFW halo with DYNESTY, with a free stellar Sersic index | R: The inner rotation curve requires a high stellar Sersic index (n >~ 5) in all four galaxies, total log M* = 10.3 - 11.0 | F: All four galaxies contain a massive compact stellar component, likely a bulge | **supported**
- H: Is turbulence in the discs driven by stellar feedback or gravitational instabilities? | E: Compare observed dispersions with Krumholz et al. models and compare SNII injectable energy with turbulent energy | R: Gravity-driven model overestimates turbulence; SN energy matches with eta ~ 0.1 for three galaxies and 0.001 - 0.01 for BRI1335-0417 | F: Stellar feedback alone can sustain the observed turbulence | **supported**
- H: How much dark matter do these discs contain within the [CII] extent? | E: Mass decomposition with NFW halo with fbar from 1e-6 to 0.187 | R: Posteriors peak near the lower prior edge (baryon dominated), but gas and halo are degenerate and halo masses have large uncertainties | F: Galaxies are baryon dominated in the inner regions; halo mass is poorly constrained | **partially**
- H: Where do the galaxies lie on local scaling relations? | E: Place them on the baryonic Tully-Fisher, ETG analogue Tully-Fisher and SHMR diagrams | R: Shifted to higher velocities than the local BTFR; overlap the local ETG relation once gas is added to stellar mass; consistent with the abundance-matching SHMR | F: The galaxies are likely progenitors of local ETGs and had assembled most baryons in the inner regions by z ~ 4.5 | **partially**

## Reasoning

- Why this data: sample chosen for the best SNR and angular and spectral resolution available in the archive  
  > "The galaxies in this sample were selected due to the quality of the data available in the ALMA archive, in terms of SNR, angular and spectral resolution." (2 Data and methods)
- Why this method: mass decomposition of rotation curves gives stellar mass without stellar continuum observations  
  > "the mass decomposition of rotation curves allows us to estimate the total stellar mass of the galaxies even without any observations of the stellar continuum" (1 Introduction)
- Alternative: free Sersic index for the surface brightness fits: did not converge for J081740 and SGP38326 gas, so n fixed to 1  
  > "the free *n* fit does not converge" (2.3 Dust and gas surface profiles)
- Alternative: BRI1335-0417 dust fitted with Sersic + PSF found no better than Sersic alone  
  > "we attempt to fit the surface brightness of the dust emission with a Sérsic + PSF components and we find no evidence that it provides a better fit." (4.1 Compact and massive stellar component)
- Alternative: wider stellar radius prior (0.2 x dust radius to 2 x [CII] radius) did not change other parameters  
  > "We find that it does not impact the estimates of the other parameters significantly" (2.6 Mass Decomposition)
- Alternative: central black hole of 1e9 Msun or a CDM halo cannot explain the inner circular speeds  
  > "However, a CDM halo cannot explain velocities of such a magnitude" (4.1 Compact and massive stellar component)
- Alternative: models with DM mass completely free give a baryon fraction above the cosmological value  
  > "we considered models with the DM mass completely free and found that the baryon fraction becomes higher than the cosmological fraction" (8 Dynamical Models)
- How they decided it was enough: a Sersic index of 1 was adopted because most converged free-n fits gave n < 2  
  > "as for the majority of our tests that have converged we find an $n<2$." (2.3 Dust and gas surface profiles)
- Limitation (authors): Sersic surface brightness model slightly overestimates outer emission  
  > "the surface brightness in the outer regions tends to be slightly overestimated by the model" (3.1 Surface Brightness)
- Limitation (authors): no resolved rest-frame optical/NIR stellar data, so stellar profile and prior knowledge unavailable  
  > "we have no significant prior knowledge on the stellar component of our sample." (2.6 Mass Decomposition)
- Limitation (authors): BRI1335-0417 gas mass only an upper limit because f_bar fixed to cosmological value  
  > "we do not have a strong constrain in the gas mass of BRI1335-0417" (3.4.2 Stellar Feedback)
- Limitation (authors): alpha_CO and CO line ratios highly uncertain  
  > "We highlight the fact that both of these numbers are highly uncertain even in the local Universe" (2.6 Mass Decomposition)
- Caveat (inferred, ours): Stellar mass, gas mass and halo mass are partly degenerate; the stellar bulge conclusion rests on a Sersic index prior of 0.2 - 10 and an assumed spherical stellar shape
- Caveat (inferred, ours): Fixing f_bar to 0.187 for BRI1335-0417 makes its masses prior-driven rather than measured
- Caveat (inferred, ours): Gas mass is scaled from a single literature CO luminosity with an unconstrained normalisation, so the SN energy budget inherits that uncertainty
- Caveat (inferred, ours): Only four heterogeneous galaxies, selected by archive data quality, so scaling-relation positions are weak evidence
- Caveat (inferred, ours): Disc heights of 0.3 and 1.0 kpc are assumed, not measured

## Reproducibility

- Data public (paper): ALMA data are public in the ALMA Science Archive  
  > "The data underlying this article are public and available in the ALMA Science Archive" (Data Availability)
- Products in archive: _not stated_
- Code: Processed data (ADC-corrected rotation curves, dust and [CII] moment-0 maps) and scripts to produce the figures are on Zenodo (DOI 10.5281/zenodo.10707348)  
  > "along with the scripts to produce the Figures in this paper are made available at Zenodo" (Data Availability)
- Missing: ALMA correlator setup, array configurations and calibration/imaging parameters (only in Roman-Oliveira et al. 2023)
- Missing: DYNESTY configuration and likelihood for the rotation-curve fit
- Missing: Mapping of project codes to galaxies
- Missing: Whether the Zenodo scripts include the DYNESTY fits or only the figure plotting
- Data volume (inferred): Raw data for five projects probably tens of GB; processed Zenodo products (rotation curves and moment-0 maps) are small
- Score (inferred): 4/5, Public ALMA data, processed products and figure scripts on Zenodo, and a fully specified fitting setup with priors; limited by upstream calibration/imaging and kinematics being in the earlier paper and unspecified likelihood and sampler settings for the decomposition.
- Rediscovery candidate: yes, Data are public, processed rotation curves and moment-0 maps are released, priors and model equations are given, and the main results are numeric (masses, fractions, eta).

## Links

- Method: (cite: romanoliveira23) (ALMA data reduction, imaging and 3DBarolo rotation curves and dispersion profiles used here)
- Method: (cite: marasco19) (residual-asymmetry effective uncertainty for the Sersic fits)
- Method: (cite: krumholz18) (analytical gravity- and feedback-driven turbulence models)
- Method: (cite: bacchini20) (supernova energy turbulence model)
- Method: (cite: terzic05) (density-potential relation for Sersic stellar component)
- Method: (cite: diteodoro15) (3DBarolo kinematic fitting)
- Companion: (cite: tsukui24) (analysis of [CII] and dust emission of BRI1335-0417 suggesting a strong bar)
- Companion: (cite: fraternali21) (two z = 4.5 galaxies on the ETG analogue Tully-Fisher relation)
- Companion: (cite: blandhawthorn23) (baryon concentration thresholds for stable bar formation)
- Related: MASSIVE survey
- Related: ATLAS3D
- Related: SPARC

## Checks

```json
{
 "quotes": 136,
 "quotes_ok": 136,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 5,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 16,
 "numeric_problems": 0,
 "fill": {
  "facts": 137,
  "stated": 89,
  "rate": 0.65
 },
 "evidence_ok": true
}
```
