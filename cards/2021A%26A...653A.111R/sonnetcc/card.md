# The ALPINE-ALMA [CII] survey. The contribution of major mergers to the galaxy mass assembly at z ∼ 5

`2021A&A...653A.111R` | Astronomy and Astrophysics 2021 | first author: Romano, M. | arXiv: 2107.10856 | DOI: 10.1051/0004-6361/202141306

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type large_program_or_survey

## Science

- Fields: high_z_galaxies
- Question: What fraction of z~5 main-sequence galaxies are undergoing major mergers (from ALPINE [CII] morpho-kinematics), how does it evolve with cosmic time, and what merger rate and mass-assembly contribution does it imply  
  > "The aim of this work is to derive the fraction of galaxies undergoing a major merger" (4.1 The fraction of major mergers in ALPINE)
- Target **ALPINE [CII]-detected galaxies (75 of 118 targets) in COSMOS and E-CDFS**: coordinates _not stated_; z/distance 4.4<z<5.9 (avoiding 4.6<z<5.1)  
  > "have secure spectroscopic redshifts from the VIMOS UltraDeep Survey" (2 Data); "resulting in 75 \[CII\] detections (S/N$>$3.5) out of 118 ALPINE targets" (2 Data); distance from spectroscopic redshifts from VUDS and DEIMOS 10K surveys; z_[CII] from the ALMA line  
  > "have secure spectroscopic redshifts from the VIMOS UltraDeep Survey" (2 Data); "resulting in 75 \[CII\] detections (S/N$>$3.5) out of 118 ALPINE targets" (2 Data)

## Data provenance

- ALMA projects: 2017.1.00428.L
- bands: Band 7 (275-373 GHz)  
  > "hours of observation with ALMA in Band 7 (275-373 GHz) during cycles 5 and 6" (2 Data)
- frequencies and spectral setup: line-only cubes with channel width ~25 km/s  
  > "line-only cubes with channel width of $\sim25~\mathrm{km~s^{-1}}$" (2 Data)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: beam size ~1'' (average beam minor axis ~0.8'')  
  > "and beam size $\sim1''$" (2 Data); "the average beam minor axis of ALPINE is $\sim0.8''$" (3.2 Physical parameters estimate)
- max recoverable scale: _not stated_
- sensitivity: not flux-limited; depth differs per pointing (per-pointing limiting flux used)  
  > "ALPINE is not a flux-limited survey as each individual ALMA pointing reaches different depths" (3.5 Accounting for completeness)
- time on source: ~70 hours for the whole ALPINE campaign  
  > "The campaign took $\sim70$ hours of observation with ALMA in Band 7 (275-373 GHz) during cycles 5 and 6" (2 Data)
- observing dates: _not stated_
- pi or archival as stated: ALPINE Large Program data release 1 (DR1) continuum and [CII] maps  
  > "we take advantage of the continuum and \[CII\] emission maps of the targets from the ALPINE data release 1" (3 Methods)
- Line: [CII] 158 micron fine-structure line (not stated)
- Other facility **HST/ACS F814W and UltraVISTA Ks imaging**: optical and near-IR cutouts used to identify multiple components and Ks-band flux ratios of merger components  
  > "the \[CII\] morphology superimposed on the HST/ACS F814W (left) and UltraVISTA (UVista) $K_s$ (right) cutouts" (3.1 Mergers characterization)
- Other facility **VUDS and DEIMOS 10K spectroscopic surveys**: spectroscopic redshifts of the ALPINE targets  
  > "have secure spectroscopic redshifts from the VIMOS UltraDeep Survey" (2 Data)
- Other facility **COSMOS/E-CDFS multiwavelength data (SED fitting)**: stellar masses and SFRs from SED fitting  
  > "archival multiwavelength data are available from the UV to the near-IR" (2 Data)
- External data: ALPINE DR1 continuum and [CII] maps and cubes  
  > "we take advantage of the continuum and \[CII\] emission maps of the targets from the ALPINE data release 1" (3 Methods) [from (cite: Bethermin20)]
- External data: Stellar masses of the merging systems from SED fitting  
  > "stellar mass of the merging system as a whole through SED-fitting measurements (cite: Faisst20)" (3.4 Description of the merger sample) [from (cite: Faisst20)]
- External data: Previous visual morpho-kinematic classification of the 75 [CII] sources  
  > "performed a preliminary morphological and kinematic classification of the 75 ALPINE targets" (2.1 Previous morpho-kinematic classifications) [from (cite: LeFevre20)]
- External data: [CII] luminosity function of UV-selected ALPINE targets (completeness weights)  
  > "is the \[CII\] luminosity function derived from the UV-selected central ALPINE targets (cite: Yan20)" (3.5 Accounting for completeness) [from (cite: Yan20)]
- External data: Major merger fractions at z<4 from pair counts (COSMOS close pairs, VVDS/VUDS/MASSIVE, MUSE, CANDELS)  
  > "evaluated the major merger fraction from a sample of close pairs drawn from the COSMOS survey" (4.2 Cosmic evolution of the major merger fraction) [from (cite: deRavel09; Xu12; Lopez13; Tasca14; Ventou17; Duncan19)]
- External data: Merger timescale prescriptions T_MM  
  > "we compare the results obtained with the merger timescales provided by (cite: Kitzbichler08), (cite: Jiang14) and (cite: Snyder17)" (4.3 Galaxy major merger rate) [from (cite: Kitzbichler08; Jiang14; Snyder17)]
- External data: Galaxy stellar mass function fits used for number densities  
  > "we exploit the GSMFs best-fit parameters from (cite: Mortlock15), (cite: Santini12) and (cite: Davidzon17)" (4.4 Merger rate density) [from (cite: Mortlock15; Santini12; Davidzon17)]
- External data: Cosmic star-formation rate density and sSFR evolution for comparison  
  > "we also show the star-formation rate density (SFRD) from (cite: Madau14)" (4.6 The major merger mass accretion rate density) [from (cite: Madau14; Speagle14; Tasca15; Khusanova21)]
- Simulation/model as data: EAGLE major merger fraction parameterization (Qu17), compared with the observed merger fraction  
  > "the best-fit parameterization of the major merger fraction found by (cite: Qu17)" (4.2 Cosmic evolution of the major merger fraction)
- Simulation/model as data: EMERGE merger rate and merger rate density predictions (Oleary21)  
  > "We also show the merger rate predictions found by (cite: Oleary21) using the results from the Empirical ModEl for the foRmation of GalaxiEs" (4.3 Galaxy major merger rate)

## Processing

### Calibration

- pipeline or manual: standard CASA pipeline (ALPINE survey reduction)  
  > "The collected ALMA data were reduced and calibrated using the standard Common Astronomy Software Applications (CASA; (cite: McMullin07)) pipeline" (2 Data)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: yes: ALPINE DR1 products (maps and cubes) used  
  > "we take advantage of the continuum and \[CII\] emission maps of the targets from the ALPINE data release 1" (3 Methods)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: pixel scale ~0.15''  
  > "with a pixel scale of $\sim0.15''$" (2 Data)
- image size: _not stated_
- masking: pixels below 3 sigma (rms of the moment-0 map) masked for moment-1 and moment-2  
  > "By masking all the pixels below $3\sigma$ (where $\sigma$ is the rms estimated in the moment-0 map)" (3 Methods)
- multiscale scales: _not stated_
- continuum subtraction: UVCONTSUB in the uv-plane: model fitted to visibilities with line channels masked, then subtracted from the cubes  
  > "The continuum was first estimated in the uv-plane by masking the spectral channels containing line emission" (3 Methods)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: moment-1 and moment-2 maps smoothed by bilinear interpolation (display)  
  > "Both the moment-1 and moment-2 maps are smoothed by using a bilinear interpolation." (3.1 Mergers characterization)
- final beam: beam size ~1''  
  > "and beam size $\sim1''$" (2 Data)
- final rms: _not stated_

### Inherited from earlier work

- Survey description, observation and data processing, and multiwavelength analysis  
  > "For a more in-depth description of the overall ALPINE survey, the observation and data processing, and the multiwavelength analysis see (cite: LeFevre20), (cite: Bethermin20) and (cite: Faisst20), respectively." (2 Data) [from (cite: LeFevre20), (cite: Bethermin20), (cite: Faisst20)]
- Procedure to determine the line-emission channel range for each [CII]-detected galaxy  
  > "For a detailed description of the procedure used to estimate the range of spectral channels containing line emission for all the \[CII\]-detected galaxies, see Section 6.1 in (cite: Bethermin20)." (3 Methods (footnote)) [from Section 6.1 in (cite: Bethermin20)]
- Morpho-kinematic class definitions (rotator, merger, extended/compact dispersion dominated, weak) and prior results  
  > "based on the same classification criteria used in (cite: LeFevre20) and on the results by (cite: Jones21)" (2.1 Previous morpho-kinematic classifications) [from (cite: LeFevre20); (cite: Jones21)]
- Definition of component size as circularized effective radius r_e  
  > "Following (cite: Fujimoto20), we refer to the merging component size as the circularized effective radius" (3.2 Physical parameters estimate) [from (cite: Fujimoto20)]
- Building moment-0 maps of individual merger components by collapsing their channels  
  > "Similarly to what has been done in (cite: Ginolfi20), the latter maps are obtained by collapsing the channels including the emission of the individual components." (3.2 Physical parameters estimate) [from (cite: Ginolfi20)]
- [CII] luminosity relation  
  > "We compute the \[CII\] luminosities by following (cite: Solomon92)" (3.5 Accounting for completeness) [from (cite: Solomon92)]
- Stellar mass gain per merger and mass accretion rate density formalism  
  > "Following (cite: Duncan19), we assume that the increase in stellar mass for each merger and at each redshift is given by" (4.6 The major merger mass accretion rate density) [from (cite: Duncan19); (cite: Mundy17)]

### Not stated but needed to reproduce (our reading)

- Per-source line-channel ranges and DR1 product versions (deferred to Bethermin20 Section 6.1)
- The objective criteria and thresholds behind the visual merger classification, and who classified each source
- How the multi-component Gaussian decomposition of each [CII] spectrum was done (fitting tool, initial guesses, number of components, rms estimation)
- Position angle, centre and exact pseudo-slit used for each PVD (only a default of 3'' length and 5 pixel width is given)
- The limiting flux or luminosity L_lim per ALPINE pointing and the luminosity function parameters used in the completeness weights
- The non-linear least-squares implementation, starting values and weighting for fitting f_MM(z), R_MM(z) and Gamma_MM(z), and the exact literature data points and errors included
- Coefficients T0, f1, f2 of the Kitzbichler08 timescale and the normalisation used for the Jiang14 timescale
- How sources were assigned to the z~4.5 and z~5.5 bins and how the Poisson errors were combined into the quoted asymmetric errors
- The values of N_p,corr per source (individual completeness weights)

## Analysis recipe

1. **Build moment maps from the DR1 line cubes**: Sum the line channels to get moment-0, then compute moment-1 and moment-2 with pixels below 3 sigma masked  
  > "the spectral channels that included the emission line were summed up to produce the velocity-integrated intensity (moment-0) maps" (3 Methods)
   - software: CASA
   - parameter: 3 sigma cut (sigma = rms of the moment-0 map) for moment-1 and moment-2  
  > "By masking all the pixels below $3\sigma$ (where $\sigma$ is the rms estimated in the moment-0 map)" (3 Methods)
   - fitting: _not stated_
   - validation: Choice of 3 sigma instead of the earlier 2 sigma contours stated not to change final results significantly  
  > "however, we find that this choice does not significantly change our final results" (3 Methods)
2. **Fit 2D Gaussians to the moment-0 maps**: One 2D Gaussian per source, or one per resolved component for mergers  
  > "we fit one 2D Gaussian component to each source in the moment-0 map" (3 Methods)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Produce position-velocity diagrams**: PVDs along the major-velocity-gradient axis and perpendicular to it, centred on the Gaussian-fit position  
  > "we decide to produce the two PVDs with the major axis oriented along the direction of major velocity gradient in the moment-1 map, and with the minor axis perpendicular to the major one" (3 Methods)
   - software: CASA
   - parameter: averaging width 5 pixels, pseudo-slit length 3'' unless otherwise stated  
  > "with an averaging width of five pixels and a pseudo-slit length of $3''$ (if not otherwise stated)" (3 Methods)
   - fitting: _not stated_
   - validation: _not stated_
4. **Extract and decompose integrated [CII] spectra**: Spatially integrated 1D spectrum within 3 sigma moment-0 contours, modeled with single- and multi-component Gaussians  
  > "we extract the spatially-integrated 1D \[CII\] spectrum of each target within the $3\sigma$ contours at the position of the source from the moment-0 map" (3 Methods); "modeled with a single and a multiple-component Gaussian function" (3.1 Mergers characterization)
   - software: CASA
   - fitting: Gaussian component fits to the spectrum; sampler, priors and likelihood not stated  
  > "modeled with a single and a multiple-component Gaussian function" (3.1 Mergers characterization)
   - validation: Single-Gaussian flux compared with the multicomponent flux for the example source  
  > "even though with a single Gaussian function we find an integrated flux of the line that is comparable with that obtained from the multicomponent fit" (3.1 Mergers characterization)
5. **Classify sources and select robust mergers**: Visual inspection of ancillary images, moment maps, channel maps, spectra and PVDs, plus S/N, velocity and distance criteria  
  > "we visually inspect the ancillary data, the intensity maps, the velocity and velocity dispersion fields" (3.3 Comparison with previous classifications)
   - parameter: minor component S/N >= 3 (integrated flux divided by rms times FWHM)  
  > "We thus consider as mergers only those systems for which the minor (in terms of the \[CII\] integrated flux) component has S/N$\geq3$." (3.1 Mergers characterization)
   - parameter: velocity separation <= 500 km/s  
  > "we decide to consider as mergers only those systems in which the components are separated by no more than $\mathrm{\Delta v\leq500~km~s^{-1}}$" (3.4 Description of the merger sample)
   - parameter: projected-distance threshold ~2.1 kpc (average [CII] size) for secure mergers  
  > "Therefore, we use this value as a threshold to classify the secure merging systems." (3.4 Description of the merger sample)
   - assumption: A velocity separation <= 500 km/s indicates a gravitationally bound system  
  > "assuming that this is the limit for a system to be gravitationally bound" (3.4 Description of the merger sample)
   - fitting: _not stated_
   - validation: Comparison with the LeFevre20 and Jones21 classifications  
  > "we recover the same qualitative morpho-kinematic distribution of the previous analysis" (3.3 Comparison with previous classifications)
6. **Measure merger-component parameters**: [CII] and Ks flux ratios, velocity separation, projected distance r_p, and sizes r_e from 2D Gaussian fits  
  > "we compute the \[CII\] flux ratio between the major and minor components of the merger" (3.2 Physical parameters estimate); "we refer to the merging component size as the circularized effective radius" (3.2 Physical parameters estimate)
   - software: CASA
   - parameter: r_p = theta x d_A(z_m) at the mean redshift of the two components  
  > "We measure the projected distance ($r_p$) between the centers of the merger components as" (3.2 Physical parameters estimate)
   - assumption: Stellar mass of the system splits into primary and secondary with mass ratio mu = 4 as the major/minor threshold  
  > "we set $\mu=4$ as a threshold to separate major ($1\leq \mu \leq4$) from minor ($\mu>4$) mergers" (3.4 Description of the merger sample)
   - fitting: _not stated_
   - validation: Size measurements checked against Fujimoto20 for the same ALPINE galaxies  
  > "we found a good agreement with their results" (3.2 Physical parameters estimate)
7. **Derive completeness weights for minor components**: Weight each minor component by the ratio of the number density above its flux to that above the pointing's limiting flux, using the [CII] luminosity function  
  > "we apply a weight to each minor component of our sample defined as" (3.5 Accounting for completeness); "We also assume that $w_\mathrm{comp}=1$ when $L_2 > L_\mathrm{lim}$." (3.5 Accounting for completeness)
   - parameter: L_2 corresponds to F_2,[CII] = F_1,[CII]/4  
  > "$L_2$ corresponds to $F_\mathrm{2,[CII]} = F_\mathrm{1,[CII]}/4$" (3.5 Accounting for completeness)
   - fitting: _not stated_
   - validation: _not stated_
8. **Compute the major merger fraction in two redshift bins**: f_MM = 0.88 x (sum of completeness weights of mergers) / N_g in the z~4.5 and z~5.5 bins; Ks flux ratio < 4 defines major mergers  
  > "we define as major mergers those candidates for which the $K_s$-band flux ratio is smaller than 4" (4.1 The fraction of major mergers in ALPINE); "The factor 0.88 accounts for the statistical uncertainty on the real merger nature" (4.1 The fraction of major mergers in ALPINE)
   - assumption: 12% of the [CII]-ratio-only subsample is assumed to be minor mergers (from the 7 of 8 sources with mu_K < 4)  
  > "we find that 7 out of 8 sources (i.e., $\sim88\%$ of this subsample) have $\mu_K < 4$" (4.1 The fraction of major mergers in ALPINE)
   - fitting: Upper and lower limits from all mergers vs only r_p > 2 kpc, plus Poisson errors added in quadrature  
  > "we compute the corresponding Poissonian errors and add them in quadrature to the above-mentioned uncertainties" (4.1 The fraction of major mergers in ALPINE)
   - validation: Removing the two proto-cluster mergers does not significantly change the fraction  
  > "we do not find any significant change in the merger fraction at $z\sim4.5$" (4.1 The fraction of major mergers in ALPINE)
9. **Fit the cosmic evolution of the merger fraction**: Combine ALPINE points with literature fractions and fit power-law x exponential f(z) = alpha (1+z)^m exp(beta (1+z))  
  > "By using a non linear least square algorithm, we fit our data both with" (4.2 Cosmic evolution of the major merger fraction)
   - assumption: Literature samples with similar stellar masses and selection criteria are comparable; constant stellar-mass range at all redshifts  
  > "we are recovering the cosmic evolution of the merger fraction by comparing galaxies with a constant stellar mass range at all redshifts" (4.2 Cosmic evolution of the major merger fraction)
   - fitting: Non-linear least squares (no priors or sampler)  
  > "By using a non linear least square algorithm, we fit our data both with" (4.2 Cosmic evolution of the major merger fraction)
   - validation: Model comparison with the Bayesian information criterion  
  > "Taking advantage of the Bayesian information criterion (BIC)" (4.2 Cosmic evolution of the major merger fraction)
10. **Convert merger fraction to merger rate and number of mergers**: R_MM = C_merg f_MM / T_MM with three timescale prescriptions, then integrate over time for N_MM  
  > "We compute the average number of mergers a galaxy undergoes between $0<z<6$ by integrating the merger rate over time as" (4.3 Galaxy major merger rate)
   - parameter: C_merg = 1  
  > "we set $C_{\text{merg}}=1$ throughout." (4.3 Galaxy major merger rate)
   - assumption: Merger timescales T_MM from Kitzbichler08, Jiang14 (H(z)^-1/3, normalised to Kitzbichler08 at z=0) and Snyder17 (2.4 (1+z)^-2)  
  > "We then compare our results with the cosmic evolution of several expected merger rates from simulations." (4.3 Galaxy major merger rate)
   - fitting: Same combined power-law and exponential form fitted to R_MM(z)  
  > "fit the resulting data with the same functional form used for the merger fraction" (4.3 Galaxy major merger rate)
   - validation: Compared with Hopkins10, Rodriguez15, Oleary21 and Dekel13 simulated rates  
  > "We then compare our results with the cosmic evolution of several expected merger rates from simulations." (4.3 Galaxy major merger rate)
11. **Compute the merger rate density**: Gamma_MM = f_MM n(z) / T_MM with n(z) from integrating GSMFs from log M = 9 to 11  
  > "We thus integrate these functions from $\mathrm{log}(M_{*}/M_{\odot})=9$ to $\mathrm{log}(M_{*}/M_{\odot})=11$" (4.4 Merger rate density)
   - parameter: GSMF parameters perturbed 10^4 times; 16th and 84th percentiles as 1 sigma on n(z)  
  > "We repeat this procedure 10$^{4}$ times, recomputing the integrated number densities at each step." (4.4 Merger rate density)
   - fitting: Power-law Gamma_0 (1+z)^gamma fitted to the density points  
  > "with a power-law function we obtain $\Gamma_0 = (2.40\pm0.63) \times 10^{-4}$" (4.4 Merger rate density)
   - validation: Compared with Mundy17 power-law and EMERGE predictions  
  > "As evident, our data points are comparable with the results by (cite: Mundy17)." (4.4 Merger rate density)
12. **Compare merger and star-formation mass growth**: Specific mass accretion rate = R_MM x 0.5 compared with sSFR; mass accretion rate density rho_MM compared with SFRD  
  > "we just take the best-fitting functions to the cosmic evolution of the merger rate and multiply them by a factor $\sim0.5$" (4.5 The major merger specific mass accretion rate)
   - assumption: Average inverse mass ratio ~0.5; SFRD converted from Salpeter to Chabrier IMF by factor 0.63  
  > "To convert SFRs from (cite: Salpeter55) to Chabrier IMF we multiply by 0.63" (Footnote 15)
   - fitting: Combined power-law and exponential, or double power-law, fits to rho_MM, compared by BIC  
  > "we find no significant differences between the two functional forms when comparing them with a BIC statistics" (4.6 The major merger mass accretion rate density)
   - validation: Compared with Illustris-based rho_ill  
  > "the computed $\rho_{\text{ill}}$ is comparable with our findings" (4.6 The major merger mass accretion rate density)

## Software

- **CASA (pipeline)** : ALPINE reduction and calibration  
  > "The collected ALMA data were reduced and calibrated using the standard Common Astronomy Software Applications (CASA; (cite: McMullin07)) pipeline" (2 Data)
- **CASA UVCONTSUB** : uv-plane continuum subtraction to make line-only cubes  
  > "The continuum was first estimated in the uv-plane by masking the spectral channels containing line emission" (3 Methods)
- **CASA IMMOMENTS** : moment-0 map creation  
  > "the spectral channels that included the emission line were summed up to produce the velocity-integrated intensity (moment-0) maps" (3 Methods)
- **CASA IMFIT** : 2D Gaussian fits to moment-0 maps  
  > "we fit one 2D Gaussian component to each source in the moment-0 map" (3 Methods)
- **CASA IMPV** : position-velocity diagrams  
  > "to produce the PVDs along the major and minor axis with the CASA" (3 Methods)
- **CASA SPECFLUX** : spatially-integrated [CII] spectra  
  > "we extract the spatially-integrated 1D \[CII\] spectrum of each target within the $3\sigma$ contours at the position of the source from the moment-0 map" (3 Methods)
- **3DBarolo** : tilted-ring fits in the earlier Jones21 classification (not run in this paper)  
  > "by using the tilted ring fitting code" (2.1 Previous morpho-kinematic classifications)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of mergers among ALPINE [CII] detections | 23 of 75 (~31%) | not stated | sources | 5 | $\sim31\%$, 23 out of 75 \[CII\]-detected sources |
| Average [CII] size of ALPINE galaxies | ~2.1 | not stated | kpc | 6 | we find an average \[CII\] size of $\sim2.1$ kpc |
| Fraction of Ks/[CII]-ratio sources with mu_K < 4 | 7 of 8 (~88%) | not stated | sources | 8 | we find that 7 out of 8 sources (i.e., $\sim88\%$ of this subsample) have $\mu_K < 4$ |
| Major merger fraction f_MM at z~4.5 and z~5.5 | 0.44 (z~4.5) and 0.34 (z~5.5) | +0.11/-0.16 (z~4.5); +0.10/-0.13 (z~5.5) | dimensionless | 8 | We find major merger fractions $f_{\text{MM}}=0.44^{+0.11}_{-0.16}$ and $f_{\text{MM}}=0.34^{+0.10}_{-0.13}$ at $z\sim4.5$ and $z\sim5.5$, respectively |
| Increase of f_MM from the completeness correction | ~30% higher than without correction | not stated | percent | 8 | we recover a merger fraction $\sim30\%$ higher than obtained if not accounting for completeness corrections |
| Best-fit alpha, m, beta of f_MM(z) | alpha = 0.024, m = 4.083, beta = -0.797 | +/-0.003, +/-0.501, +/-0.189 | dimensionless | 9 | the parameters of this fit are $\alpha = 0.024\pm0.003$, $m=4.083\pm0.501$ and $\beta = -0.797\pm0.189$ |
| Merger rate R_MM at z~4.5 and z~5.5 with the Kitzbichler08 timescale | ~0.09 and ~0.07 | not stated | Gyr^-1 | 10 | we obtain $R_{\text{MM}}\sim0.09$ and $R_{\text{MM}}\sim0.07$ Gyr$^{-1}$ at $z\sim4.5$ and $z\sim5.5$, respectively |
| Average number of mergers down to z=0, Kitzbichler08 and Jiang14 timescales | 0.5 to 1.4 | not stated | mergers per galaxy | 10 | is low, ranging between 0.5 and 1.4 down to $z=0$ |
| Average number of mergers since z=6 with the Snyder17 timescale | ~8 | not stated | mergers per galaxy | 10 | reaching $N_{\text{MM}}\sim8$ at the present day |
| Power-law fit of merger rate density (Kitzbichler08 timescale) | Gamma_0 = 2.40e-4, gamma = -0.16 | +/-0.63e-4, +/-0.23 | Gamma_0 in Gyr^-1 Mpc^-3; gamma dimensionless | 11 | $\Gamma_0 = (2.40\pm0.63) \times 10^{-4}$ and $\gamma = -0.16\pm0.23$ |

## Qualitative findings

- [CII] is less affected by dust extinction than optical tracers, so it can reveal dusty merger components obscured in the optical  
  > "As this line is less affected by dust extinction than optical tracers" (1 Introduction)
- With the Kitzbichler08 and Jiang14 timescales major mergers contribute less than 10% of mass assembly relative to star formation at all redshifts  
  > "major mergers seem to contribute less than $10\%$ to the galaxy mass assembly compared to the star formation mechanism at all redshifts" (4.6 The major merger mass accretion rate density)
- Star formation dominates the specific mass growth at all epochs, but mergers become comparable at z>3 for T_MM proportional to (1+z)^-2  
  > "star formation seems to be the dominant mode of mass growth at all epochs" (4.5 The major merger specific mass accretion rate)

## Claim tuples

- H: A significant fraction of z~5 main-sequence galaxies are undergoing major mergers | E: Morpho-kinematic analysis of ALPINE [CII] cubes with completeness and minor-merger corrections | R: f_MM = 0.44 (+0.11/-0.16) at z~4.5 and 0.34 (+0.10/-0.13) at z~5.5 | F: Significant merging activity exists in the early Universe | **supported**
- H: The merger fraction keeps rising to high redshift versus peaks and declines | E: Fit ALPINE plus literature fractions with a power-law and a power-law x exponential, compared by BIC | R: Delta BIC > 10 favours the combined form; alpha = 0.024, m = 4.083, beta = -0.797 | F: Rapid rise from z=0, peak at z~3, slow decrease toward earlier epochs | **supported**
- H: The inferred merger rate depends on the adopted merger timescale | E: Convert f_MM to R_MM with the Kitzbichler08, Jiang14 and Snyder17 timescales | R: R_MM at z~5 ranges from ~0.1 to ~4.0 per Gyr and N_MM from <1 to ~8 | F: Results are strongly dependent on the T_MM choice | **supported**
- H: Major mergers contribute significantly to galaxy mass assembly at z>4 | E: Compare specific mass accretion rate and mass accretion rate density with sSFR and SFRD | R: Mergers are comparable to star formation at z>3-4 only for T_MM proportional to (1+z)^-2; otherwise below 10% | F: Contribution is uncertain and dependent on merger timescale; an evolving T_MM agrees with simulations | **partially**

## Reasoning

- Why this data: [CII] gives 3D morpho-kinematic information and is less affected by dust than optical tracers; first use of [CII] for the major merger fraction  
  > "Here, for the first time, we make use of the rest-frame FIR \[CII\] line to compute the major merger fraction in the early Universe." (1 Introduction)
- Why this method: 3 sigma pixel cut chosen over 2 sigma to avoid spurious emission  
  > "we decide to select only the pixels above the $3\sigma$ level in order to be less affected by possible spurious emissions" (3 Methods)
- Alternative: Conselice09 data not included in the evolution fit because they do not separate major and minor mergers  
  > "as they do not differentiate between major and minor mergers, we do not include them in the computation of the cosmic evolution of the merger fraction" (4.2 Cosmic evolution of the major merger fraction)
- Alternative: Plain power-law f(z) = f0 (1+z)^m rejected in favour of a combined power-law and exponential form  
  > "Taking advantage of the Bayesian information criterion (BIC)" (4.2 Cosmic evolution of the major merger fraction)
- How they decided it was enough: _not stated_
- Limitation (authors): Low spatial resolution prevents constraining the minor merger fraction at z~5  
  > "the relatively low spatial resolution of the ALPINE survey does not allow us to constrain the minor merger fraction" (4.1 The fraction of major mergers in ALPINE)
- Limitation (authors): Stellar mass only known for the whole merging system and Ks ratios available for only 9 of 23 mergers  
  > "The $K_s$-band ratio is available for 9 out of 23 mergers" (4.1 The fraction of major mergers in ALPINE)
- Limitation (authors): Lack of constraints on the merger timescale prevents firm conclusions  
  > "the lack of further constraints on the most suitable choice for the merger timescale prevent us from providing firm conclusions" (5.2 The contribution of major mergers to the galaxy mass-assembly)
- Caveat (inferred, ours): Merger identification is visual and partly subjective; no blind or independent re-classification test is reported
- Caveat (inferred, ours): Major/minor split relies on the Ks-band flux ratio, which at z~5.5 is below the Balmer break and a poor mass proxy
- Caveat (inferred, ours): Only 9 of 23 mergers have a Ks ratio; the 0.88 factor comes from 8 sources
- Caveat (inferred, ours): Mixing literature pair fractions with different selections may bias the evolution fit
- Caveat (inferred, ours): Many downstream numbers (R_MM, rho_MM) are dominated by the choice of T_MM

## Reproducibility

- Data public (paper): ALPINE DR1 data are available online  
  > "DR1 data are available at <https://cesam.lam.fr/a2c2s/data_release.php>." (Footnote 3)
- Products in archive: _not stated_
- Code: _not stated_
- Missing: Objective merger-classification procedure and the per-source Gaussian spectral decompositions
- Missing: Per-pointing limiting fluxes and luminosity-function inputs for the completeness weights
- Missing: Exact list of literature data points, errors and fit implementation for the evolution fits
- Missing: Timescale coefficients and GSMF choices per redshift bin
- Data volume (inferred): 75 ALPINE DR1 line cubes plus continuum maps; likely a few GB to tens of GB from the public DR1 release
- Score (inferred): 3/5, DR1 data are public and the main CASA steps and thresholds are named, and many numbers are given, but the visual classification, spectral decompositions, completeness inputs and literature fits cannot be fully redone from the text.
- Rediscovery candidate: no, Data are public and results numeric, but the merger identification is visual and subjective and several inputs are unstated, so the recipe is not complete enough to redo.

## Links

- Method: (cite: Bethermin20) (ALPINE DR1 data processing and line-channel selection)
- Method: (cite: LeFevre20) (ALPINE survey description and the original visual morpho-kinematic classification)
- Method: (cite: Faisst20) (Multiwavelength SED-fitting stellar masses and SFRs)
- Method: (cite: Jones21) (3DBarolo tilted-ring classification of ALPINE galaxies)
- Method: (cite: Fujimoto20) (Definition and measurement of [CII] effective radii)
- Companion: (cite: Ginolfi20) (Detailed analysis of an ALPINE merging system at z~4.6)
- Companion: (cite: Jones20) (Detailed analysis of an ALPINE merging system at z~4.6)
- Companion: (cite: Yan20) ([CII] luminosity function used for completeness weights)
- Companion: (cite: Khusanova21) (ALPINE SFRD and sSFR comparison)
- Related: ALPINE
- Related: COSMOS
- Related: E-CDFS
- Related: VUDS
- Related: DEIMOS 10K Spectroscopic Survey
- Related: UltraVISTA
- Related: CANDELS

## Checks

```json
{
 "quotes": 120,
 "quotes_ok": 120,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 130,
  "stated": 96,
  "rate": 0.738
 },
 "evidence_ok": true
}
```
