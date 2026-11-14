# No Impact of Core-scale Magnetic Field, Turbulence, or Velocity Gradient on Sizes of Protostellar Disks in Orion A

`2021ApJ...916...97Y` | The Astrophysical Journal 2021 | first author: Yen, Hsi-Wei | arXiv: 2106.00148 | DOI: 10.3847/1538-4357/ac0723

Card schema 1.0 | model gemini-4-argon | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks, star_formation
- Question: Investigate the dependences of protostellar disk sizes and fluxes in Orion A on core-scale magnetic field, turbulence, and gas motions to determine the key mechanisms regulating disk formation and evolution.  
  > "We compared the sizes and fluxes of a sample of protostellar disks in Orion A measured with the ALMA 0.87 mm continuum data from the VANDAM survey with the physical properties of their ambient environments" (Abstract); "We then discuss the dependences of the disk properties on the magnetic field, turbulence, and gas motions on the scale of dense cores to investigate the key mechanisms regulating the disk formation and evolution." (Introduction)
- Target **79 individual protostars in 56 protostellar sources in Orion A (HOPS sample)**: coordinates See Table 7 (e.g., HOPS-96 at 05:35:29.718 -04:58:48.60)  
  > "This leads to a sample of 56 protostellar sources for the present study." (Sample); "In total, there are 79 individual protostars in our sample." (Sample); "assuming that the observations are able to resolve disks with their diameters larger than the synthesized beam, which is $\sim$43 au at the distances to our sample protostars." (ALMA 0.87 mm continuum); z/distance 0.11 arcsec corresponds to ~43 au (39-49 au in Orion A and B)  
  > "This leads to a sample of 56 protostellar sources for the present study." (Sample); "In total, there are 79 individual protostars in our sample." (Sample); "assuming that the observations are able to resolve disks with their diameters larger than the synthesized beam, which is $\sim$43 au at the distances to our sample protostars." (ALMA 0.87 mm continuum); distance from _not stated_

## Data provenance

- ALMA projects: _none stated_
- bands: 0.87 mm  
  > "The ALMA observations of the VANDAM survey are conducted at 0.87 mm and have a synthesized beam of 0.11$''$, corresponding to 39–49 au at the distances to Orion A and B." (Sample)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.11'' (39-49 au)  
  > "The ALMA observations of the VANDAM survey are conducted at 0.87 mm and have a synthesized beam of 0.11$''$, corresponding to 39–49 au at the distances to Orion A and B." (Sample)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: publicly available survey data from the VANDAM survey (Table 6 in Tobin et al. 2020)  
  > "We compared the sizes and fluxes of a sample of protostellar disks in Orion A measured with the ALMA 0.87 mm continuum data from the VANDAM survey" (Abstract); "We obtained the properties of the circumstellar disks around our sample protostars, including disk radii, orientations projected on the plane of the sky, and fluxes from Table 6 in (cite: Tobin20)." (ALMA 0.87 mm continuum)
- Other facility **Green Bank Telescope (GBT) / Green Bank Ammonia Survey (GAS)**: NH3 emission property maps at 23 GHz (kinetic temperature, line width, centroid line-of-sight velocity) with 32'' FWHM beam and 10.6'' pixel size  
  > "The Orion A molecular clouds have also been mapped in the NH$_3$ emission with the Green Bank Ammonia Survey (cite: Friesen17; Kirk17), which is a survey to map the NH$_3$ emission at 23 GHz" (Sample); "we retrieved the NH$_3$ property maps, including kinetic temperature, line width, and centroid line-of-sight velocity, of Orion A from the publicly released datasets of GAS" (GBT NH$_3$ emission); "The pixel size of the NH$_3$ property maps is 10.6$''$ ($\sim$4200 au)." (GBT NH$_3$ emission)
- Other facility **James Clerk Maxwell Telescope (JCMT) / SCUPOL survey**: Stokes IQU maps of polarized thermal dust continuum emission at 850 um smoothed to 20'' angular resolution with 10'' pixel size  
  > "we retrieved the Stokes IQU maps at 850 $\mu$m of OMC-2 and -3 obtained with the JCMT SCUPOL survey from the SCUBA Polarimeter Legacy Catalogue" (JCMT polarized 850 $\mu$m continuum); "These Stokes IQU maps were smoothed to have an angular resolution of 20$\ensuremath{''}$ (cite: Matthews09)." (JCMT polarized 850 $\mu$m continuum); "we computed mean Stokes Q and U intensities averaged over 3 by 3 pixels around each sample protostar, where the pixel size is 10$\ensuremath{''}$" (JCMT polarized 850 $\mu$m continuum)
- External data: Circumstellar disk properties (deconvolved radii, orientations, and 0.87 mm continuum fluxes) from elliptical Gaussian fits in Table 6, and protostellar classifications  
  > "We obtained the properties of the circumstellar disks around our sample protostars, including disk radii, orientations projected on the plane of the sky, and fluxes from Table 6 in (cite: Tobin20)." (ALMA 0.87 mm continuum); "Among them, 25 are Class 0 protostars, 13 are Class I protostars, and 18 are flat-spectrum protostars (cite: Tobin20)." (Sample) [from (cite: Tobin20)]
- External data: Bolometric temperatures (T_bol) of the sample protostars  
  > "Table notes: $T_{\rm bol}$ is the bolometric temperature (cite: Furlan16)." (Table 7) [from (cite: Furlan16)]
- External data: Mean size (0.06 pc or 13,000 au) and standard deviation (6900 au) of dense cores in Orion A identified in JCMT 850 um continuum maps  
  > "The mean size of the dense cores in Orion A identified in the JCMT 850 $\mu$m continuum map is 13 000 au (or 0.06 pc) with a standard deviation of 6900 au (cite: Lane16; Kirk17)." (GBT NH$_3$ emission) [from (cite: Lane16; Kirk17)]

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
- final beam: 0.11'' (~43 au)  
  > "The ALMA observations of the VANDAM survey are conducted at 0.87 mm and have a synthesized beam of 0.11$''$, corresponding to 39–49 au at the distances to Orion A and B." (Sample); "assuming that the observations are able to resolve disks with their diameters larger than the synthesized beam, which is $\sim$43 au at the distances to our sample protostars." (ALMA 0.87 mm continuum)
- final rms: _not stated_

### Inherited from earlier work

- Definition of single protostars as having no other protostars within 10^4 au on the plane of the sky  
  > "where single protostars are defined as having no other protostars within 10$^4$ au on the plane of the sky, the same as the definition in (cite: Tobin20)." (Sample) [from (cite: Tobin20)]
- Disk radius definition as the 2 sigma width of the fitted elliptical Gaussian function to 0.87 mm continuum emission  
  > "Following the definition in (cite: Tobin20), we define the disk radius to be the 2$\sigma$ width of the fitted Gaussian function." (ALMA 0.87 mm continuum) [from (cite: Tobin20)]
- Method for fitting a linear velocity gradient to centroid line-of-sight velocity maps  
  > "We followed the method in (cite: Goodman93) and fitted a linear velocity gradient to 3 by 3 pixels around the protostellar position in the centroid line-of-sight velocity map." (GBT NH$_3$ emission) [from (cite: Goodman93)]
- Unsharp masking method for removing large-scale magnetic field structures and noise subtraction for intrinsic angular dispersion  
  > "To remove contributions by large-scale magnetic field structures, we adopted the method similar to unsharp masking, as introduced in, for example, (cite: Pattle17) and (cite: WangJ19)." (JCMT polarized 850 $\mu$m continuum); "As discussed in (cite: WangJ19), we then subtracted the uncertainties in the polarization orientations due to the noise in the data ($\delta\theta_\sigma$) from the measured angular dispersion ($\delta\theta_{\rm ob}$)" (JCMT polarized 850 $\mu$m continuum) [from (cite: Pattle17; WangJ19)]
- Dust mass opacity of 0.012 cm^2 g^-1 (including gas-to-dust ratio of 100) and line-of-sight cloud length of 0.06 pc with 50% uncertainty  
  > "Then we converted the optical depth to column density on the assumption of a dust mass opacity of 0.012 cm$^{2}$ g$^{-1}$, which includes a gas-to-dust mass ratio of 100." (JCMT polarized 850 $\mu$m continuum); "These values are the same as those adopted in the studies of the dense cores in Orion A (cite: Lane16; Kirk17)." (JCMT polarized 850 $\mu$m continuum); "We assumed a constant length of 0.06 pc of all the sample sources and a 50% uncertainty in the length" (JCMT polarized 850 $\mu$m continuum) [from (cite: Lane16; Kirk17)]
- Equations for expected tidal truncation radius in a binary system  
  > "We calculated the expected truncation radius in a binary system with equal masses and a non-eccentric binary orbit following the equations in (cite: Manara19)." (Potential biases due to multiplicity and evolution) [from (cite: Manara19)]
- Monte Carlo calculation of 3D misalignment angle probability distributions from 2D projected angles  
  > "To test the significance of this correlation considering the projection effects, we followed calculations in (cite: Galametz20) to compute the probability distribution of the 3D misalignment angles of these 12 Class 0 protostars." (Dependence on turbulence and magnetic field) [from (cite: Galametz20)]

### Not stated but needed to reproduce (our reading)

- Exact distances adopted for each individual protostar in the sample to convert angular sizes to physical au and pc scales
- Specific data release version of the GBT GAS Orion A property maps
- Exact formula or lookup table used to interpolate the small-sample bias correction factors (given only for N=4, 7, 10) across all N values of polarization detections

## Analysis recipe

1. **Select sample and compile ALMA 0.87 mm disk properties**: Cross-match VANDAM survey 0.87 mm ALMA continuum detections with GBT GAS NH3 detections in Orion A, and extract deconvolved disk radii, position angles, and fluxes from Table 6 of Tobin et al. (2020).  
  > "From the VANDAM sample, we selected those protostellar sources which are detected in both the 0.87 mm continuum emission with ALMA and the NH$_3$ emission with GBT." (Sample); "We obtained the properties of the circumstellar disks around our sample protostars, including disk radii, orientations projected on the plane of the sky, and fluxes from Table 6 in (cite: Tobin20)." (ALMA 0.87 mm continuum)
   - parameter: Disk radius = 2 sigma width of fitted elliptical Gaussian; upper limit = 1 sigma width of synthesized beam for unresolved sources  
  > "Following the definition in (cite: Tobin20), we define the disk radius to be the 2$\sigma$ width of the fitted Gaussian function." (ALMA 0.87 mm continuum); "For unresolved sources, the upper limits of their disk radii are adopted to be the 1$\sigma$ width of the synthesized beam" (ALMA 0.87 mm continuum)
   - assumption: Observations resolve disks with diameters larger than the synthesized beam (~43 au); envelope contamination is minimal  
  > "assuming that the observations are able to resolve disks with their diameters larger than the synthesized beam, which is $\sim$43 au at the distances to our sample protostars." (ALMA 0.87 mm continuum); "As discussed in (cite: Tobin20), the contamination from protostellar envelopes is minimal in these measurements because large-scale envelopes are resolved out" (ALMA 0.87 mm continuum)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure core-scale non-thermal line width and velocity gradient from GBT NH3 maps**: Average kinetic temperature and line width over 3x3 pixels (10.6'' pixel size, ~0.06 pc core scale) around each protostar in GAS NH3 maps, compute non-thermal line width, and fit a linear velocity gradient to the 3x3 pixel centroid velocity map following Goodman et al. (1993).  
  > "For each protostar in our sample, we measured the mean kinematic temperature and line width over 3 by 3 pixels around the protostellar position." (GBT NH$_3$ emission); "Then the non-thermal line width ($\delta V_{\rm nt}$) on the core scale around each protostar was computed as $$\begin{equation}
\delta V_{\rm nt} = \sqrt{{\delta V_{\rm ob}}^2 - \frac{kT_{\rm k}}{m_{\rm NH_3}}},
\end{equation}$$" (GBT NH$_3$ emission); "We followed the method in (cite: Goodman93) and fitted a linear velocity gradient to 3 by 3 pixels around the protostellar position in the centroid line-of-sight velocity map." (GBT NH$_3$ emission)
   - parameter: 3 by 3 pixels box (pixel size 10.6'', ~4200 au, representing 0.06 pc core scale)  
  > "The pixel size of the NH$_3$ property maps is 10.6$''$ ($\sim$4200 au)." (GBT NH$_3$ emission); " Nevertheless, we simply measured the properties over the core scale of 0.06 pc uniformly for all the sample protostars." (GBT NH$_3$ emission)
   - assumption: Uniform core scale of 0.06 pc (13,000 au) based on JCMT 850 um dense core mean size in Orion A  
  > "The mean size of the dense cores in Orion A identified in the JCMT 850 $\mu$m continuum map is 13 000 au (or 0.06 pc) with a standard deviation of 6900 au (cite: Lane16; Kirk17)." (GBT NH$_3$ emission)
   - fitting: Linear velocity gradient fit over 3x3 pixels following Goodman et al. (1993)  
  > "We followed the method in (cite: Goodman93) and fitted a linear velocity gradient to 3 by 3 pixels around the protostellar position in the centroid line-of-sight velocity map." (GBT NH$_3$ emission)
   - validation: _not stated_
3. **Measure core-scale magnetic field orientation and angular dispersion from JCMT SCUPOL 850 um maps**: Extract polarization detections (SNR > 3 in Stokes I and polarized intensity), rotate by 90 deg to get B-field orientation, average Stokes Q and U over 3x3 pixels (within 15'') for mean B-field orientation, and use unsharp masking (subtracting 3x3 pixel local mean orientation) for sources with >3 detections within 15'' to compute intrinsic angular dispersion.  
  > "We extracted polarization detections from the Stokes IQU maps with the detection criteria of the signal-to-noise ratios of Stokes I and polarized intensities both above three." (JCMT polarized 850 $\mu$m continuum); "From the polarization detections, we computed mean Stokes Q and U intensities averaged over 3 by 3 pixels around each sample protostar, where the pixel size is 10$\ensuremath{''}$" (JCMT polarized 850 $\mu$m continuum); "For the 34 protostars with more than three nearby polarization detections within 15$\ensuremath{''}$, we also measured its angle dispersion of the magnetic field orientations on the core scale of 0.06 pc." (JCMT polarized 850 $\mu$m continuum)
   - parameter: SNR > 3 for Stokes I and polarized intensity; 3x3 pixels (10'' pixel size, within 15''); >3 detections required for angular dispersion  
  > "We extracted polarization detections from the Stokes IQU maps with the detection criteria of the signal-to-noise ratios of Stokes I and polarized intensities both above three." (JCMT polarized 850 $\mu$m continuum); "For the 34 protostars with more than three nearby polarization detections within 15$\ensuremath{''}$, we also measured its angle dispersion of the magnetic field orientations on the core scale of 0.06 pc." (JCMT polarized 850 $\mu$m continuum)
   - assumption: Mean polarization orientation of 3x3 pixels centered at each detection represents the large-scale magnetic field orientation  
  > "we computed the mean Stokes Q and U intensities and thus the mean polarization orientation of 3 by 3 pixels centered at that detection, which is assumed to be the large-scale magnetic field orientation" (JCMT polarized 850 $\mu$m continuum)
   - fitting: _not stated_
   - validation: Monte Carlo simulations of N random Gaussian data points to correct for small-sample bias (underestimation of 13%, 6%, 4% and uncertainties of 39%, 29%, 23% for N = 4, 7, 10)  
  > "We generated simulated samples with N numbers of data points randomly drawn from a Gaussian distribution, and calculated the standard deviations of the simulated samples." (JCMT polarized 850 $\mu$m continuum); "We found that the standard deviations tend to be underestimated by 13%, 6%, and 4% when N is 4, 7, 10, and the uncertainties in the calculated standard deviations due to the small number of data points were estimated to be 39%, 29%, and 23%, respectively." (JCMT polarized 850 $\mu$m continuum)
4. **Derive plane-of-sky magnetic field strength and normalized mass-to-flux ratio**: Estimate 850 um optical depth and column density from JCMT Stokes I mean intensity on the core scale, convert to volume density, and apply the Davis-Chandrasekhar-Fermi (DCF) equation for B_pos and compute normalized mass-to-flux ratio lambda.  
  > "Finally, we derived the magnetic field strengths on the core scale projected on the plane of the sky ($B_{\rm pos}$) in our sample protostars with the Davis–Chandrasekhar–Fermi method (cite: Davis51; Chandrasekhar53)" (JCMT polarized 850 $\mu$m continuum); "We estimated $\rho$ from the mean intensity of the 850 $\mu$m continuum emission on the core scale in the Stokes I maps obtained from the JCMT SCUPOL survey." (JCMT polarized 850 $\mu$m continuum); "The normalized mass-to-flux ratio ($\lambda$) was also computed for each sample protostar as, $$\begin{equation}
\lambda = 2\pi \sqrt{G}\frac{\Sigma}{B_{\rm pos}}, 
\end{equation}$$" (JCMT polarized 850 $\mu$m continuum)
   - parameter: DCF correction factor xi = 0.5  
  > "where $\xi$ was adopted to be 0.5 to correct for inhomogeneous and complex magnetic field and density structures along the line of sight (cite: Ostriker01)" (JCMT polarized 850 $\mu$m continuum)
   - assumption: Dust temperature equals NH3 kinetic temperature; dust mass opacity = 0.012 cm^2 g^-1 (including gas-to-dust ratio of 100); line-of-sight cloud length = 0.06 pc with 50% uncertainty  
  > "For each sample protostar, we first measured the optical depth of the 850 $\mu$m continuum, assuming that the dust temperature is the same as the kinetic temperature measured with the GAS NH$_3$ data." (JCMT polarized 850 $\mu$m continuum); "Then we converted the optical depth to column density on the assumption of a dust mass opacity of 0.012 cm$^{2}$ g$^{-1}$, which includes a gas-to-dust mass ratio of 100." (JCMT polarized 850 $\mu$m continuum); "We assumed a constant length of 0.06 pc of all the sample sources and a 50% uncertainty in the length" (JCMT polarized 850 $\mu$m continuum)
   - fitting: _not stated_
   - validation: _not stated_
5. **Filter sample for binary tidal truncation bias**: Compare disk radii against projected distance to the nearest companion and theoretical equal-mass circular binary truncation radii from Manara et al. (2019); exclude protostars with separations < 800 au.  
  > "We calculated the expected truncation radius in a binary system with equal masses and a non-eccentric binary orbit following the equations in (cite: Manara19)." (Potential biases due to multiplicity and evolution); "In the following discussions, we exclude the protostars with separations smaller than 800 au from our sample to avoid a bias due to binary interaction. The remaining sample consists of 50 individual protostars." (Potential biases due to multiplicity and evolution)
   - parameter: Separation threshold = 800 au (leaving 50 individual protostars)  
  > "In the following discussions, we exclude the protostars with separations smaller than 800 au from our sample to avoid a bias due to binary interaction. The remaining sample consists of 50 individual protostars." (Potential biases due to multiplicity and evolution)
   - assumption: Equal masses and non-eccentric binary orbit for expected truncation radius curve  
  > "We calculated the expected truncation radius in a binary system with equal masses and a non-eccentric binary orbit following the equations in (cite: Manara19)." (Potential biases due to multiplicity and evolution)
   - fitting: _not stated_
   - validation: Tested changing separation threshold to 500 or 1000 au and compared disk radius distributions of singles vs multiples beyond 800 au  
  > "We have confirmed that our discussions are not sensitive to this selection criterion based on the separation, and changing this selection criterion to a separation of 500 or 1000 au does not affect our results and conclusions." (Potential biases due to multiplicity and evolution); "There is no statistically significant difference between the disk radius distributions of the singles and multiples." (Potential biases due to multiplicity and evolution)
6. **Statistical correlation analysis and 3D deprojection Monte Carlo test**: Compute linear Pearson correlation (IDL CORRELATE) and Spearman's rank correlation (IDL R_CORRELATE) between disk radii/fluxes and core-scale parameters for the 50-protostar subsample and Class 0 (T_bol < 70 K) subset; run 5000 Monte Carlo iterations deprojecting 2D misalignment angles to 3D for the 12 Class 0 protostars.  
  > "We computed the linear Pearson correlation coefficients between the disk radii and these parameters of the turbulence and the magnetic fields." (Dependence on turbulence and magnetic field); "We also computed the Spearman’s rank correlation, which is more sensitive to a non-linear correlation." (Dependence on turbulence and magnetic field); "To test the significance of this correlation considering the projection effects, we followed calculations in (cite: Galametz20) to compute the probability distribution of the 3D misalignment angles of these 12 Class 0 protostars." (Dependence on turbulence and magnetic field)
   - software: IDL
   - parameter: 5000 Monte Carlo iterations for 12 Class 0 protostars (60,000 simulated data points); T_bol < 70 K threshold for young/Class 0 subset  
  > "We repeated this process for 5000 times, so we had 60 000 simulated data points." (Dependence on turbulence and magnetic field)
   - assumption: Magnetic field and rotational axis are randomly oriented in 3D space, and measured disk radius is not affected by projection  
  > "For each data point of the Class 0 protostars, we first inferred its 3D misalignment angle assuming that the magnetic field and the rotational axis are randomly oriented in 3D space, and the measured disk radius was not affected by projection." (Dependence on turbulence and magnetic field)
   - fitting: _not stated_
   - validation: Evaluated Pearson correlation distribution across the 5000 Monte Carlo 3D realizations  
  > "From the distribution of all the computed coefficients, we estimated the linear Pearson correlation coefficient between the misalignment angles and the disk radii to be 0.2$\pm$0.2 after considering the projection effects." (Dependence on turbulence and magnetic field)

## Software

- **IDL** : Computing linear Pearson correlation (CORRELATE function) and Spearman's rank correlation (R_CORRELATE function)  
  > "The linear Pearson correlation was computed with the IDL function CORRELATE" (Footnote 3 (Dependence on turbulence and magnetic field)); "The Spearman’s rank was computed with the IDL function R_CORRELATE" (Footnote 4 (Dependence on turbulence and magnetic field))

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Median disk radius of Class 0 protostars in subsample | 50 | not stated | au | 5 | The median disk radii of the Class 0, Class I, and flat-spectrum in our subsample are 50 au, 57 au, and 40 au, respectively. |
| Median disk radius of Class I protostars in subsample | 57 | not stated | au | 5 | The median disk radii of the Class 0, Class I, and flat-spectrum in our subsample are 50 au, 57 au, and 40 au, respectively. |
| Median disk radius of flat-spectrum protostars in subsample | 40 | not stated | au | 5 | The median disk radii of the Class 0, Class I, and flat-spectrum in our subsample are 50 au, 57 au, and 40 au, respectively. |
| Pearson correlation coefficient (|r|) between disk radius and core-scale turbulence/magnetic field parameters (B_pos, delta_V_nt, delta_theta_B, lambda) | <= 0.17 | not stated | dimensionless | 6 | The absolute values of the correlation coefficients are mostly less than 0.1 and at most 0.17. |
| Pearson correlation coefficient between disk radius and 2D B-field/rotational-axis misalignment (full subsample) | 0.06 | not stated | dimensionless | 6 | The linear Pearson correlation coefficient was computed to be 0.06, and the calculation of the Spearman’s rank correlation also suggests that there is no significant correlation. |
| Pearson correlation coefficient between disk radius and 2D B-field/rotational-axis misalignment (T_bol < 70 K subsample) | 0.4 | not stated | dimensionless | 6 | The Pearson correlation coefficient was computed to be 0.4, and the calculation of the Spearman’s rank correlation shows a correlation coefficient of 0.6 at a confidence level of 98%. |
| Spearman rank correlation coefficient between disk radius and 2D B-field/rotational-axis misalignment (T_bol < 70 K subsample) | 0.6 | 98% confidence level | dimensionless | 6 | The Pearson correlation coefficient was computed to be 0.4, and the calculation of the Spearman’s rank correlation shows a correlation coefficient of 0.6 at a confidence level of 98%. |
| Pearson correlation coefficient between disk radius and 3D deprojected misalignment angle (Class 0 / T_bol < 70 K subsample) | 0.2 | 0.2 | dimensionless | 6 | From the distribution of all the computed coefficients, we estimated the linear Pearson correlation coefficient between the misalignment angles and the disk radii to be 0.2$\pm$0.2 after considering the projection effects. |
| Pearson correlation coefficient (|r|) between disk radius and core-scale velocity gradient parameters | < 0.1 | not stated | dimensionless | 6 | The linear Pearson correlation coefficients between the disk radii and these parameters related to the velocity gradients on the core scales were computed, and the absolute values were all below 0.1. |
| Pearson correlation coefficient between core-scale velocity gradient magnitude and non-thermal line width | 0.68 | not stated | dimensionless | 6 | We found that the magnitudes of the velocity gradients are correlated with the non-thermal line widths (Fig. 4d) with a Pearson correlation coefficients of 0.68. |
| Spearman rank correlation coefficient between core-scale velocity gradient magnitude and non-thermal line width | 0.56 | >99% confidence level | dimensionless | 6 | The calculation of the Spearman’s rank correlation also suggests a correlation coefficient of 0.56 at a confidence level higher than 99%. |

## Qualitative findings

- Protostellar disks in multiple systems with companion separations smaller than 800 au tend to have smaller radii, consistent with tidal truncation.  
  > "We found that the radii of the protostellar disks in multiple systems with smaller separations tend to be smaller, when the separations are smaller than 800 au. This trend is likely due to the tidal truncation in multiple systems." (Summary)
- Disk radii do not correlate with bolometric temperature in the subsample, spanning an order of magnitude at similar evolutionary stages, implying dust evolution is not the dominant mechanism setting the 0.87 mm disk size distribution.  
  > "There is no clear sign of decreasing disk radii with time evolution, possibly due to the smaller sample size, as compared to the full VANDAM sample." (Potential biases due to multiplicity and evolution); "Thus, dust evolution is unlikely a dominant mechanism in determining the disk size distribution observed in the millimeter continuum." (Potential biases due to multiplicity and evolution)
- There is no significant correlation between disk radii (or 0.87 mm continuum fluxes) and core-scale non-thermal line width, magnetic field orientation angular dispersion, magnetic field strength, mass-to-flux ratio, or B-field/rotational-axis misalignment.  
  > "We did not find any significant dependence of the disk radii and continuum fluxes on a single parameter on the core scale, such as the non-thermal line width, magnetic field orientation and strength, or magnitude and orientation of the velocity gradient." (Abstract)
- The lack of correlation between disk radii and core-scale turbulence, magnetic field strength, or misalignment is consistent with non-ideal MHD simulations where disk size is self-regulated by magnetic braking and ambipolar/non-ideal diffusion.  
  > "Our results of no clear dependence of the disk radii on these parameters are more consistent with the expectation from non-ideal MHD simulations of disk formation in collapsing cores, where the disk size is self-regulated by magnetic braking and diffusion" (Abstract)
- Core-scale velocity gradient magnitudes correlate positively with non-thermal line widths but not with disk radii, indicating that 0.06 pc scale velocity gradients trace turbulent motion rather than large-scale core rotation.  
  > "Among these parameters, we only found a positive correlation between the magnitude of the velocity gradient and the non-thermal line width. Thus, the observed velocity gradients are more likely related to turbulent motion but not large-scale rotation." (Abstract)

## Claim tuples

- H: Circumstellar disks in multiple protostellar systems with close companions are truncated by dynamical interactions. | E: Compare ALMA 0.87 mm disk radii as a function of projected separation to the nearest protostellar companion against analytical equal-mass circular binary tidal truncation radii from Manara et al. (2019). | R: Disks with separations smaller than 800 au tend to have smaller radii whose upper envelope matches the expected binary truncation radius, whereas disks with separations > 800 au have expected truncation radii more than a factor of two larger than their disk radii. | F: Disk radii around protostars with separations < 800 au are affected by binary dynamical interaction, while those beyond 800 au are not. | **supported**
- H: Protostellar disk sizes and fluxes depend on core-scale turbulence, magnetic field strength, or misalignment between the magnetic field and disk rotational axis, as predicted by ideal MHD models with turbulence/misalignment. | E: Compute Pearson and Spearman rank correlations between ALMA 0.87 mm disk radii/fluxes and core-scale (0.06 pc) non-thermal line width, magnetic field angular dispersion, plane-of-sky magnetic field strength, mass-to-flux ratio, and B-field/rotational-axis misalignment (including 3D Monte Carlo deprojection for Class 0 sources). | R: Absolute Pearson correlation coefficients are <= 0.17 with confidence levels < 50% for the subsample, and the apparent 2D misalignment correlation for Class 0 sources (r = 0.4) drops to r = 0.2 +/- 0.2 (~1 sigma) after 3D projection correction. | F: Disk radii and continuum fluxes show no significant dependence on single core-scale turbulence or magnetic field parameters, which is more consistent with non-ideal MHD self-regulation of disk sizes than ideal MHD turbulence/misalignment models. | **supported**
- H: Protostellar disk radii are proportional to core-scale rotation traced by large-scale (0.06 pc) NH3 velocity gradients. | E: Compare ALMA disk radii with the magnitude, alignment angle, and disk-major-axis-projected magnitude of core-scale NH3 velocity gradients, and test the correlation between velocity gradient magnitude and non-thermal line width. | R: Pearson correlation coefficients between disk radii and velocity gradient parameters are all < 0.1 in absolute value, whereas velocity gradient magnitude correlates strongly with non-thermal line width (Pearson r = 0.68, Spearman r = 0.56 at >99% confidence). | F: Core-scale velocity gradients on 0.06 pc scales do not correlate with disk radii and likely trace turbulent motion rather than coherent large-scale core rotation. | **supported**

## Reasoning

- Why this data: Publicly available surveys (ALMA VANDAM, GBT GAS, JCMT SCUPOL) toward Orion A provide uniform multi-scale measurements of protostellar disks (~100 au) and ambient core-scale (~0.06 pc) gas kinematics, turbulence, and magnetic fields for a statistical sample of 56 protostellar systems.  
  > "Therefore, in this work, we make use of publicly available survey data and compare the properties of a sample of protostellar disks in the Orion star-forming regions measured with the Atacama Large Millimeter/submillimeter Array (ALMA) with the physical conditions in their ambient environment observed with single-dish telescopes." (Introduction)
- Why this method: Averaging GBT NH3 and JCMT SCUPOL properties over 3x3 pixels uniformly samples the typical 0.06 pc (13,000 au) dense core scale in Orion A without relying on core identification in complex, lower-resolution maps; unsharp masking removes large-scale B-field curvature before applying the DCF method.  
  > "Thus, our measurements averaged over 3 by 3 pixels can represent the mean properties on the typical core scale in Orion A. We did not perform a core identification using the NH$_3$ data, considering the limited resolution of the NH$_3$ data and the complex structures in Orion A" (GBT NH$_3$ emission); "To remove contributions by large-scale magnetic field structures, we adopted the method similar to unsharp masking, as introduced in, for example, (cite: Pattle17) and (cite: WangJ19)." (JCMT polarized 850 $\mu$m continuum)
- Alternative: Core identification using GBT NH3 data or JCMT 850 um core catalogs was rejected in favor of uniform 3x3 pixel averaging around each protostar because of limited NH3 resolution, complex cloud structures, and some protostars not being associated with JCMT-identified cores.  
  > "We did not perform a core identification using the NH$_3$ data, considering the limited resolution of the NH$_3$ data and the complex structures in Orion A, as discussed in (cite: Lane16) and (cite: Kirk17)." (GBT NH$_3$ emission); "We also found that a few protostars in our sample are not associated with the dense cores identified with the JCMT 850 $\mu$m continuum data by (cite: Lane16)." (GBT NH$_3$ emission)
- Alternative: Alternative companion separation cutoffs of 500 au and 1000 au (instead of 800 au) were tested and found not to affect the results or conclusions.  
  > "We have confirmed that our discussions are not sensitive to this selection criterion based on the separation, and changing this selection criterion to a separation of 500 or 1000 au does not affect our results and conclusions." (Potential biases due to multiplicity and evolution)
- Alternative: Dust evolution as the dominant driver of the 0.87 mm disk radius distribution was rejected because disk radii do not decrease with bolometric temperature in the subsample and vary by an order of magnitude at similar evolutionary stages.  
  > "On the contrary, the disk radii of protostars at similar evolutionary stages can differ by an order of magnitude. Thus, dust evolution is unlikely a dominant mechanism in determining the disk size distribution observed in the millimeter continuum." (Potential biases due to multiplicity and evolution)
- How they decided it was enough: _not stated_
- Limitation (authors): Past dynamical interactions (fly-bys or close encounters in the Orion A stellar cluster) and local net angular momentum on scales smaller than 0.06 pc cannot be probed or excluded with the current data.  
  > "Nevertheless, we cannot exclude the influences on the observed disk size distribution by dynamical interaction in a stellar cluster or amounts of angular momentum on the core scale, which cannot be probed with the current data." (Abstract); "However, we cannot exclude the possibility of having a fly-by or close encounters in the past." (Effects of crowded environments)
- Limitation (authors): ALMA 0.87 mm dust continuum emission only traces dusty disks, whose sizes can differ from gaseous disks due to optical depth, radial drift, and grain growth.  
  > "We note that the ALMA 0.87 mm continuum emission only traces dusty disks. Sizes of dusty disks can be different from those of gaseous disks due to different opacities between lines and continuum, dust drift, and grain growth (cite: Birnstiel10; Facchini17)." (Potential biases due to multiplicity and evolution)
- Limitation (authors): Line-of-sight cloud lengths are unknown and assumed to be a constant 0.06 pc with 50% uncertainty.  
  > "The lengths of the clouds along the line of sight are unknown. We assumed a constant length of 0.06 pc of all the sample sources and a 50% uncertainty in the length" (JCMT polarized 850 $\mu$m continuum)
- Limitation (authors): Unequal binary mass ratios or eccentric orbits could cause tidal truncation at separations > 800 au, though low disk-to-separation ratios (< 0.02) would require rare eccentricities > 0.8.  
  > "The truncation radius can be smaller if the mass ratio is not unity or the binary orbit is eccentric in a binary system, which could result in small disks (cite: Artymowicz94; Pichardo05). This possibility cannot be ruled out in our sample." (Potential biases due to multiplicity and evolution)
- Limitation (authors): Small numbers of polarization detections within 15'' bias the standard deviation of magnetic field orientations and introduce large uncertainties (23% to 39%).  
  > "We note that the calculated standard deviation can be biased due to the small number of detections included." (JCMT polarized 850 $\mu$m continuum)
- Caveat (inferred, ours): No raw or calibrated ALMA data were processed in this paper; all ALMA disk measurements are taken directly from Table 6 of Tobin et al. (2020), so any systematic biases in Gaussian fitting of resolved/marginally resolved disks are inherited.
- Caveat (inferred, ours): There is a recurring typo in the Abstract and Summary stating the core scale as '0.6 pc' whereas Section 3, Section 4, and Section 5 state '0.06 pc' (13,000 au).
- Caveat (inferred, ours): Upper limits on unresolved disks (<18 au) are included in the sample; the paper does not specify how left-censored data (upper limits) were treated in the IDL CORRELATE and R_CORRELATE calculations.

## Reproducibility

- Data public (paper): All three survey datasets (VANDAM Table 6, GBT GAS property maps on Harvard Dataverse, and JCMT SCUPOL Legacy Catalogue at CADC) are publicly available, and all derived measurements for the 79 protostars are published in Table 7.  
  > "We made use of the publicly available science data from the VANDAM, GAS, and SCUPOL surveys" (Summary); "we retrieved the NH$_3$ property maps, including kinetic temperature, line width, and centroid line-of-sight velocity, of Orion A from the publicly released datasets of GAS" (GBT NH$_3$ emission); "we retrieved the Stokes IQU maps at 850 $\mu$m of OMC-2 and -3 obtained with the JCMT SCUPOL survey from the SCUBA Polarimeter Legacy Catalogue" (JCMT polarized 850 $\mu$m continuum)
- Products in archive: GAS maps at https://dataverse.harvard.edu/dataverse/GAS_Project and SCUPOL maps at http://www.cadc-ccda.hia-iha.nrc-cnrc.gc.ca/community/scupollegacy/  
  > "https://dataverse.harvard.edu/dataverse/GAS_Project" (Dependence on turbulence and magnetic field); "http://www.cadc-ccda.hia-iha.nrc-cnrc.gc.ca/community/scupollegacy/" (Dependence on turbulence and magnetic field)
- Missing: Exact treatment of disk radius upper limits (<18 au) in the Pearson and Spearman correlation calculations
- Missing: Exact interpolation of the small-N bias correction factor for N values other than 4, 7, and 10 in the magnetic field angular dispersion calculation
- Missing: Exact per-source distances used to convert angular scales to physical scales
- Data volume (inferred): < 1 GB (uses published catalog tables and single-dish 2D FITS property maps from GAS and SCUPOL)
- Score (inferred): 9/5, All input catalogs/maps are publicly hosted with direct URLs, equations and pixel-averaging boxes (3x3 pixels) are explicitly defined, software functions (IDL CORRELATE and R_CORRELATE) are named, and the complete intermediate derived dataset for all 79 sources is provided in Table 7.
- Rediscovery candidate: yes, All input survey data and Table 7 derived measurements are public, the analysis recipe is analytical and statistical, and the main results are exact correlation coefficients and median disk sizes.

## Links

- Method: (cite: Goodman93) (Linear velocity gradient fitting method applied to 3x3 pixel NH3 centroid velocity maps)
- Method: (cite: Pattle17) (Unsharp masking method for removing large-scale magnetic field structure from polarization maps)
- Method: (cite: WangJ19) (Unsharp masking and noise subtraction for intrinsic magnetic field angular dispersion)
- Method: (cite: Davis51; Chandrasekhar53) (Davis-Chandrasekhar-Fermi (DCF) method for estimating plane-of-sky magnetic field strength)
- Method: (cite: Ostriker01) (DCF correction factor xi = 0.5 for inhomogeneous magnetic field and density structure)
- Method: (cite: Manara19) (Analytical equations for tidal truncation radius of circumstellar disks in binary systems)
- Method: (cite: Galametz20) (Monte Carlo method for deprojecting 2D misalignment angles into 3D probability distributions)
- Companion: (cite: Tobin20) (VANDAM survey paper providing the ALMA 0.87 mm continuum disk radii, orientations, fluxes (Table 6), and multiplicity classifications)
- Companion: (cite: Friesen17; Kirk17) (Green Bank Ammonia Survey (GAS) papers providing the Orion A NH3 property maps and dense core properties)
- Companion: (cite: Matthews09) (JCMT SCUPOL Legacy Catalogue paper providing the 850 um Stokes IQU polarization maps of OMC-2/3)
- Related: VLA/ALMA Nascent Disk and Multiplicity (VANDAM) Survey
- Related: Green Bank Ammonia Survey (GAS)
- Related: SCUPOL / SCUBA Polarimeter Legacy Catalogue
- Related: Herschel Orion Protostar Survey (HOPS)

## Checks

```json
{
 "quotes": 121,
 "quotes_ok": 121,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 7,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2015.1.00041.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 99,
  "stated": 59,
  "rate": 0.596
 },
 "evidence_ok": true
}
```
