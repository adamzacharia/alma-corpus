# The ALMA Survey of 70 µm Dark High-mass Clumps in Early Stages (ASHES). XIII. Core Mass Function, Lifetime, and Growth of Prestellar Cores

`2026ApJ...997..155M` | The Astrophysical Journal 2026 | first author: Morii, Kaho | arXiv: 2512.00147 | DOI: 10.3847/1538-4357/ae25f6

Card schema 1.0 | model gemini-4-argon | depth full | type large_program_or_survey

## Science

- Fields: star_formation, milky_way_ism
- Question: What are the universality, power-law slope, lifetime, and mass growth properties of the prestellar core mass function (CMF) in the earliest stages of high-mass star formation within 70 μm dark IRDC clumps?  
  > "However, the universality of the CMF and its relationship to the initial mass function (IMF) remain unclear." (Abstract); "We study the CMF in the earliest stage of high-mass star formation using 461 prestellar core candidates and 254 protostellar cores as a part of the ALMA Survey of 70 μm Dark High-mass Clumps in Early Stages (ASHES)." (Abstract)
- Target **ASHES sample of thirty-nine 70 μm-dark IRDC clumps**: coordinates _not stated_; z/distance > a few kpc  
  > "However, IRDCs are typically located far from the Sun (i.e., $>$a few kpc)" (Introduction); "The ASHES-sample consists of thirty-nine 70 μm-dark IRDC clumps with the potential for high-mass star formation (cite: Morii23)." (Observations and Data); distance from _not stated_
- Target **G010.991–00.082**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **G014.492–00.139**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **G018.801–00.297**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **G024.010+00.489**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **G028.564–00.236**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.01539.S, 2017.1.00716.S, 2018.1.00192.S
- bands: Band 6 (~1.3 mm)  
  > "Observations were carried out with ALMA in Band 6 ($\sim$224 GHz; $\sim$1.3 mm) through three cycles: Cycle 3 (2015.1.01539.S, PI: P. Sanhueza), Cycle 5 (2017.1.00716.S, PI: P. Sanhueza), and Cycle 6 (2018.1.00192.S, PI: P. Sanhueza)." (Observations and Data)
- frequencies and spectral setup: ~224 GHz; velocity resolution ~1.3 km s^-1 for CO, H2CO, CH3OH, HC3N, C18O; 0.17 km s^-1 for DCO+, N2D+  
  > "Observations were carried out with ALMA in Band 6 ($\sim$224 GHz; $\sim$1.3 mm) through three cycles: Cycle 3 (2015.1.01539.S, PI: P. Sanhueza), Cycle 5 (2017.1.00716.S, PI: P. Sanhueza), and Cycle 6 (2018.1.00192.S, PI: P. Sanhueza)." (Observations and Data); "Their velocity resolutions are $\sim$1.3 km s$^{-1}$. DCO$^+$ ($J=3-2$) and N$_2$D$^+$ ($J=3-2$) with velocity resolutions of 0.17 km s$^{-1}$ are used for the virial analysis." (Observations and Data)
- continuum bandwidth: _not stated_
- arrays: 12-m array, 7-m array, Total Power (TP; for spectral line data only)  
  > "The data were taken with the main 12-m array and the Atacama Compact Array (ACA), including both the 7-m array and Total Power (TP; for spectral line data only)." (Observations and Data)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~1.2'' for continuum; 29.6'' for TP C18O  
  > "The average 1$\sigma$ rms noise level of the continuum images was $\sim$0.094 mJy beam$^{-1}$ with a beam size of $\sim$1.2$''$." (Observations and Data); "We also use TP data of the C$^{18}$O ($J= 2-1$) to estimate the velocity dispersion of the clumps, which has a velocity resolution of 1.3 km s$^{-1}$ and an angular resolution of 29.6$''$." (Observations and Data)
- max recoverable scale: _not stated_
- sensitivity: ~0.094 mJy beam^-1 (average 1sigma continuum rms)  
  > "The average 1$\sigma$ rms noise level of the continuum images was $\sim$0.094 mJy beam$^{-1}$ with a beam size of $\sim$1.2$''$." (Observations and Data)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: PI: P. Sanhueza  
  > "Observations were carried out with ALMA in Band 6 ($\sim$224 GHz; $\sim$1.3 mm) through three cycles: Cycle 3 (2015.1.01539.S, PI: P. Sanhueza), Cycle 5 (2017.1.00716.S, PI: P. Sanhueza), and Cycle 6 (2018.1.00192.S, PI: P. Sanhueza)." (Observations and Data)
- Line: CO J=2-1 (not stated)
- Line: H2CO J_{K_a, K_c} = 3_{2,2}-2_{2,1}, 3_{2,1}-2_{2,0} (not stated)
- Line: CH3OH J_K = 4_2-3_1 (not stated)
- Line: HC3N J=24-23 (not stated)
- Line: DCO+ J=3-2 (not stated)
- Line: N2D+ J=3-2 (not stated)
- Line: C18O J=2-1 (not stated)
- External data: NH3 rotational temperatures at ~5'' for cores in eleven ASHES clumps  
  > "For cores in eleven ASHES clumps, we used the rotational temperatures derived from NH$_3$ observations at $\sim$5$''$ (cite: Li23; Allingham24)." (Core Mass) [from (cite: Li23; Allingham24)]
- External data: Clump temperatures for twenty-eight clumps  
  > "For the remaining twenty-eight clumps, we adopted the clump temperature for the core mass calculation (cite: Guzman15)." (Core Mass) [from (cite: Guzman15)]
- External data: Core catalog (839 cores), continuum properties, and temperatures used for mass estimation (Table 4)  
  > "Column 3 in Table 4 in (cite: Morii23) shows the temperature used for each core in the mass estimation." (Core Mass); "By applying the dendrogram technique, implemented in `astrodendro` (cite: Rosolowsky08), to the 1.3 mm continuum images of 39 regions, we have identified 839 cores (cite: Morii23)." (Observations and Data) [from (cite: Morii23)]
- External data: Core evolutionary classifications and virial parameters  
  > "Detailed information and line setups are described in (cite: Morii24)." (Observations and Data); "Among 839 cores, either of the lines is detected from 492 cores (58.6%), and 340 cores (69.1%) have virial parameter smaller than 2, classified as gravitationally bound cores ignoring external pressure and the magnetic field (cite: Morii24)." (Observations and Data) [from (cite: Morii24)]
- External data: Dust opacity at 1.3 mm of 0.9 cm^2 g^-1  
  > "We adopt the standard gas-to-dust mass ratio of 100, and a dust opacity of 0.9 cm$^2$ g$^{-1}$ (cite: Ossenkopf94)." (Core Mass) [from (cite: Ossenkopf94)]
- External data: CMF power-law indices from the ALMA-IMF project for comparison  
  > "For comparison, we plotted the index and the uncertainties estimated in some studies of the ALMA-IMF project (cite: Nony23; Pouteau23; Louvet24)." (Power-law Index of CMFs) [from (cite: Nony23; Pouteau23; Louvet24)]

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
- primary beam correction: primary beam correction applied; core extraction restricted to primary beam response > 40%  
  > "For each mass bin, the flux of the Gaussian core was calculated from Equation [\[equ:Mass\]](#equ:Mass) considering the primary beam correction." (Completeness); "The inserted position of core center was uniformly random in a region where the primary beam response was higher than 40% to avoid cores located at the edge, consistent with the core identification process." (Completeness)
- array combination: 12 m array combined with 7 m array  
  > "Those lines are produced by combining the 12 m array data with the 7 m array data." (Observations and Data)
- smoothing: _not stated_
- final beam: ~1.2'' for continuum; 29.6'' for TP C18O  
  > "The average 1$\sigma$ rms noise level of the continuum images was $\sim$0.094 mJy beam$^{-1}$ with a beam size of $\sim$1.2$''$." (Observations and Data); "We also use TP data of the C$^{18}$O ($J= 2-1$) to estimate the velocity dispersion of the clumps, which has a velocity resolution of 1.3 km s$^{-1}$ and an angular resolution of 29.6$''$." (Observations and Data)
- final rms: ~0.094 mJy beam^-1 (average 1sigma continuum rms)  
  > "The average 1$\sigma$ rms noise level of the continuum images was $\sim$0.094 mJy beam$^{-1}$ with a beam size of $\sim$1.2$''$." (Observations and Data)

### Inherited from earlier work

- ASHES observation setup, imaging, and core identification of 839 cores  
  > "(cite: Sanhueza19) and (cite: Morii23) describe the detailed ASHES program and the observation setup." (Observations and Data); "By applying the dendrogram technique, implemented in `astrodendro` (cite: Rosolowsky08), to the 1.3 mm continuum images of 39 regions, we have identified 839 cores (cite: Morii23)." (Observations and Data) [from (cite: Sanhueza19) and (cite: Morii23)]
- Core evolutionary classification and virial analysis  
  > "We classified cores into prestellar core candidates and protostellar cores using the molecular lines. Detailed information and line setups are described in (cite: Morii24)." (Observations and Data) [from (cite: Morii24)]
- First-order optical depth check method at 1.3 mm  
  > "We checked the optical depth at 1.3 mm ($	au_{m 1.3mm}$) at first order by taking the ratio of $I_{m 1.3mm, peak} / \Omega$ to $B_{m 1.3mm}(T_{m dust})$, corresponding to 1-exp(-$	au_{m 1.3mm}$), where $I_{m 1.3mm, peak}$ is the measured peak intensity, $\Omega$ is the beam solid angle, as introduced in Appendix B of (cite: Pouteau22)." (Core Mass) [from (cite: Pouteau22)]
- Complementary cumulative distribution with variable-size bins for CMF  
  > "In addition to the standard differential histogram, to avoid arbitrariness of binning and to directly compare with other references, we also derived the complementary cumulative distribution with variable-size bins, Figure [3](#fig:cmf_prebound) (b) and 3(e), following the recommendations of (cite: MaizApellaniz05) and (cite: Reid06), the same method as (cite: Motte18_natas)." (Prestellar CMF) [from (cite: MaizApellaniz05), (cite: Reid06), (cite: Motte18_natas)]
- Maximum likelihood estimate (MLE) power-law fitting method  
  > "Also, we performed the fitting using maximum likelihood estimates (MLE; Figures [3](#fig:cmf_prebound) (c) and (f)) as developed by (cite: Clauset09), following one of the ALMA-IMF studies by (cite: Louvet24) and implemented in the Python package, `powerlaw` (cite: Alstott14)." (Prestellar CMF) [from (cite: Clauset09), (cite: Louvet24)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration and imaging parameters (e.g., CASA version, tclean weighting, robust parameter, multiscale scales, continuum subtraction), which are deferred to Sanhueza et al. (2019) and Morii et al. (2023)
- Exact astrodendro parameters (min_value, min_delta, min_npix) used for core identification and artificial core recovery tests, deferred to Morii et al. (2023)
- Individual source distances and dust temperatures for the 39 clumps / 839 cores, deferred to Table 4 of Morii et al. (2023)

## Analysis recipe

1. **Identify cores, classify evolutionary stages, and assess gravitational binding**: Extract cores from 1.3 mm continuum images of 39 regions using astrodendro (and getsf with 10 arcsec maximum size for comparison); classify into outflow cores, warm cores, and prestellar core candidates using CO (2-1) and warm gas tracers (H2CO, CH3OH, HC3N); compute virial parameters from DCO+ and N2D+ (3-2) velocity dispersions.  
  > "By applying the dendrogram technique, implemented in `astrodendro` (cite: Rosolowsky08), to the 1.3 mm continuum images of 39 regions, we have identified 839 cores (cite: Morii23)." (Observations and Data); "We classified cores into prestellar core candidates and protostellar cores using the molecular lines. Detailed information and line setups are described in (cite: Morii24)." (Observations and Data); "As we did with `astrodendro`, we ran `getsf` for 39 continuum images. In this case, we only needed to set the maximum size of the sources, which did not significantly affect the output. We set it to 10 arcsec, which is almost ten times larger than the beam size." (Core Identification: astrodendro VS getsf)
   - software: astrodendro, getsf
   - parameter: virial parameter < 2 for gravitationally bound cores; getsf maximum source size = 10 arcsec  
  > "Among 839 cores, either of the lines is detected from 492 cores (58.6%), and 340 cores (69.1%) have virial parameter smaller than 2, classified as gravitationally bound cores ignoring external pressure and the magnetic field (cite: Morii24)." (Observations and Data); "We set it to 10 arcsec, which is almost ten times larger than the beam size." (Core Identification: astrodendro VS getsf)
   - assumption: Ignore external pressure and magnetic field in virial analysis  
  > "Among 839 cores, either of the lines is detected from 492 cores (58.6%), and 340 cores (69.1%) have virial parameter smaller than 2, classified as gravitationally bound cores ignoring external pressure and the magnetic field (cite: Morii24)." (Observations and Data)
   - fitting: _not stated_
   - validation: Compared astrodendro core catalog and CMF against getsf extraction on the same 39 continuum images  
  > "To confirm our results are independent of the core identification method adopted (astrodendro), we ran `getsf` (cite: Menshchikov13; Menshchikov21), as described in Appendix [7](#sec:Appendix_coremethod), and obtain a consistent result." (Completeness)
2. **Calculate core masses and verify optically thin dust emission**: Compute core masses from 1.3 mm continuum flux density using Equation 1, and check optical depth at 1.3 mm using the ratio of peak intensity over beam solid angle to the Planck function.  
  > "The core masses are derived from the 1.3 mm dust continuum emission adopting the optically thin assumption in" (Core Mass); "We checked the optical depth at 1.3 mm ($	au_{m 1.3mm}$) at first order by taking the ratio of $I_{m 1.3mm, peak} / \Omega$ to $B_{m 1.3mm}(T_{m dust})$, corresponding to 1-exp(-$	au_{m 1.3mm}$), where $I_{m 1.3mm, peak}$ is the measured peak intensity, $\Omega$ is the beam solid angle, as introduced in Appendix B of (cite: Pouteau22)." (Core Mass)
   - parameter: gas-to-dust mass ratio R = 100; dust opacity kappa_nu = 0.9 cm^2 g^-1  
  > "We adopt the standard gas-to-dust mass ratio of 100, and a dust opacity of 0.9 cm$^2$ g$^{-1}$ (cite: Ossenkopf94)." (Core Mass)
   - assumption: Optically thin 1.3 mm dust continuum emission; NH3 rotational temperatures for 11 clumps and clump temperatures for 28 clumps  
  > "The core masses are derived from the 1.3 mm dust continuum emission adopting the optically thin assumption in (cite: Morii23)" (Core Mass); "For cores in eleven ASHES clumps, we used the rotational temperatures derived from NH$_3$ observations at $\sim$5$''$ (cite: Li23; Allingham24). For the remaining twenty-eight clumps, we adopted the clump temperature for the core mass calculation (cite: Guzman15)." (Core Mass)
   - fitting: _not stated_
   - validation: Checked 1 - exp(-tau_1.3mm) ratios, finding values < 0.08 (median 0.001), confirming optically thin condition  
  > "The cores have ratios smaller than 0.08 (median of 0.001), which is in agreement with the optically thin condition." (Core Mass)
3. **Evaluate mass completeness, apply flux recovery correction, and select final core sample**: Insert artificial Gaussian cores into continuum images at uniformly random positions where primary beam response > 40%, run astrodendro 5000 times to measure detection rate and flux recovery per mass bin, exclude 5 clumps with lowest completeness, and divide observed core masses by the recovery fraction where completeness > 0.5.  
  > "We calculated the mass completeness by inserting an artificial Gaussian core into the continuum images and varying the core mass." (Completeness); "We repeated the test 5000 times and calculated the mean detection rate per mass bin from region to region to determine the 90% completeness level." (Completeness); "Using this flux recovery profile, we corrected the observed masses by dividing them by the corresponding recovery fraction in each mass bin and region." (Completeness)
   - software: astrodendro
   - parameter: 5000 trials; primary beam response > 40%; 90% completeness threshold = 1.2 M_sun after excluding 5 clumps; flux correction applied where completeness > 0.5  
  > "The inserted position of core center was uniformly random in a region where the primary beam response was higher than 40% to avoid cores located at the edge, consistent with the core identification process." (Completeness); "After this selection, our sample ensures a 90% completeness level above 1.2 $M_\odot$, resulting in a final sample of 715 cores for the CMF analysis." (Completeness); "The correction has been applied to the mass range of each core where the completeness level is higher than 0.5, colored in Figure [2](#fig:CMF_completeness)." (Completeness)
   - assumption: Artificial cores have Gaussian profiles  
  > "We calculated the mass completeness by inserting an artificial Gaussian core into the continuum images and varying the core mass." (Completeness)
   - fitting: _not stated_
   - validation: Compared CMF slopes before and after flux recovery correction  
  > "The CMFs of the selected 715 cores before and after flux correction are shown in the middle and right panels of Figure [1](#fig:cmf-all)." (Completeness)
4. **Construct CMFs and fit power-law slopes**: Construct differential histograms (using numpy Freedman Diaconis Estimator for bin edges), variable-bin complementary cumulative distributions, and unbinned distributions; fit power-law indices above 1.2 M_sun and evaluate 1sigma uncertainties via 1000-trial Monte Carlo simulations of 50% mass uncertainties.  
  > "The bin size was determined with a task in `numpy` of *histogram bin edges* as Freedman Diaconis Estimator (fd), which takes into account data size." (Core Mass); "Also, we performed the fitting using maximum likelihood estimates (MLE; Figures [3](#fig:cmf_prebound) (c) and (f)) as developed by (cite: Clauset09), following one of the ALMA-IMF studies by (cite: Louvet24) and implemented in the Python package, `powerlaw` (cite: Alstott14)." (Prestellar CMF); "We multiplied a random value in the range of 0.5–1.5 for each core mass in one trial and produced the CMF. We repeated this simulation 1000 times and calculated a 1 sigma value coming from the mass uncertainty." (Prestellar CMF)
   - software: Numpy, powerlaw
   - parameter: M_min = 1.2 M_sun; 1000 Monte Carlo trials with mass scaling factor uniformly in 0.5-1.5  
  > "The black lines represent the best fit of the power law index above the lowest 90% completeness level of 1.2 $M_\odot$, $dN/dM \propto M^\alpha$, $N(> \mathrm{log} M) \propto M^{\alpha +1}$, or $P(m) = - rac{\alpha +1}{M_{m min}} \left(rac{m}{M_{m min}} ight)^{\alpha}$." (Prestellar CMF); "We multiplied a random value in the range of 0.5–1.5 for each core mass in one trial and produced the CMF. We repeated this simulation 1000 times and calculated a 1 sigma value coming from the mass uncertainty." (Prestellar CMF)
   - assumption: Core mass uncertainty is 50%  
  > "Considering a 50% uncertainty in core masses (Section [3.1](#sec:mass)), we performed a Monte Carlo simulation to assess how the CMF changes." (Prestellar CMF)
   - fitting: Power-law fitting to histograms/cumulative distributions and Maximum Likelihood Estimation (MLE) via powerlaw package above 1.2 M_sun  
  > "MLE determines the best-fit power-law slope directly from the unbinned data by maximizing the likelihood of the observed distribution, avoiding biases from histogram binning." (Prestellar CMF)
   - validation: Compared three different CMF representations/fitting methods (differential histogram, variable-bin cumulative distribution, and unbinned MLE)  
  > "In addition to the standard differential histogram, to avoid arbitrariness of binning and to directly compare with other references, we also derived the complementary cumulative distribution with variable-size bins, Figure [3](#fig:cmf_prebound) (b) and 3(e), following the recommendations of (cite: MaizApellaniz05) and (cite: Reid06), the same method as (cite: Motte18_natas)." (Prestellar CMF)
5. **Estimate statistical lifetime of prestellar cores as a function of mass**: Compute statistical lifetime of gravitationally bound prestellar cores relative to bound protostellar cores overall and in logarithmic mass bins using Equation 2.  
  > "Assuming a constant star formation rate throughout the cloud’s lifetime, the statistical lifetime can be derived as $$egin{equation} t_{m pre} = rac{m Number\,of\,prestellar\,core}{m Number\,of\,protostellar\,core} 	imes t_{m proto}, \label{equ:lifetime} \end{equation}$$ where $t_{m proto}$ is the reference lifetime." (Lifetime of Prestellar Cores); "In each mass bin, we counted the number of prestellar and protostellar cores and applied Equation [\[equ:lifetime\]](#equ:lifetime). Here, we limited the sample only to gravitationally bound cores." (Lifetime of Prestellar Cores)
   - parameter: reference protostellar lifetime t_proto = 0.2 Myr; freefall time t_ff ~ 3 x 10^4 yr  
  > "Due to the lack of a formal definition of classes based on Spectral Energy Distributions (SEDs) in high-mass star-forming regions, and following studies that calculated the relative number of protostellar cores with HII regions (cite: Tige17; Motte18), we adopt 0.2 Myr as the protostellar lifetime, $t_{m proto}$." (Lifetime of Prestellar Cores); "This value is $\sim$6 times longer than the freefall time of the ASHES cores, which is approximately 3$	imes$10$^4$ yr." (Lifetime of Prestellar Cores)
   - assumption: Constant star formation rate throughout the cloud's lifetime; baseline constant core mass over time, plus alternative scenarios with M_proto = 2 * M_obs (accretion onto protostar) and M_proto = 0.5 * M_obs (core growth)  
  > "Assuming a constant star formation rate throughout the cloud’s lifetime, the statistical lifetime can be derived as" (Lifetime of Prestellar Cores); "For example, if half of the initial core mass has already been accreted onto the protostar, then their initial core mass would be twice the currently observed core mass ($M_{m proto}=2 	imes M_{m obs}$)." (Lifetime of Prestellar Cores); "For example, if the initial core mass was half of the observed mass ($M_{m proto}=0.5 	imes M_{m obs}$), the estimated values are shown in Figure [5](#fig:lifetime) as blue squares." (Lifetime of Prestellar Cores)
   - fitting: _not stated_
   - validation: Tested sensitivity to core classification (excluding warm cores or including warm cores in prestellar sample) and core mass evolution scenarios (M_proto = 2 M_obs and M_proto = 0.5 M_obs)  
  > "Even when comparing the number of prestellar core candidates and cores associated with outflows (i.e., excluding warm cores from the protostellar core sample) or including warm cores in the prestellar core sample, the derived lifetime is still less than 0.1 Myr at 10 $M_\odot$." (Lifetime of Prestellar Cores)
6. **Model core mass growth and infer external mass infall rate from CMF evolution**: Compare observed bound prestellar and protostellar CMFs with Bondi-Hoyle-Lyttleton (BHL) accretion and fit a power-law external mass infall model (M_dot = C * M^p) using scipy curve_fit.  
  > "Here, we investigate the effect of external infall or core growth on the CMF, as well as the amount of external infall needed to reproduce the observed protostellar CMF from the prestellar CMF." (Core Growth and CMF); "Then, to investigate which power-law index of mass can reproduce the observed CMFs, we assumed that the external mass infall rate follows a power-law dependence on mass ($\dot{M} = C M^{p}$), where C is a constant factor and estimated the best-fit parameter $p$ using non-linear least squares fitting with `scipy`’s `curve_fit`." (Core Growth and CMF)
   - software: Scipy
   - parameter: n_cl = 4 x 10^4 cm^-3; sigma_cl = 1 km s^-1; external infall duration = 30 kyr  
  > "for the median clump density ($n_{m cl}$) of $4	imes 10^4\,m cm^{-3}$ and the median velocity dispersion of the clumps ($\sigma_{m cl}$) of $1m\,km\,s^{-1}$ (cite: Morii23)." (Core Growth and CMF); "Assuming a duration of external infall of 30 kyr, approximately free-fall time of ASHES cores, the mass infalll rate is described as" (Core Growth and CMF)
   - assumption: External mass infall rate follows a power-law dependence on core mass over a constant duration of 30 kyr  
  > "Then, to investigate which power-law index of mass can reproduce the observed CMFs, we assumed that the external mass infall rate follows a power-law dependence on mass ($\dot{M} = C M^{p}$), where C is a constant factor" (Core Growth and CMF); "Assuming a duration of external infall of 30 kyr, approximately free-fall time of ASHES cores, the mass infalll rate is described as" (Core Growth and CMF)
   - fitting: Non-linear least squares fitting with scipy's curve_fit  
  > "Then, to investigate which power-law index of mass can reproduce the observed CMFs, we assumed that the external mass infall rate follows a power-law dependence on mass ($\dot{M} = C M^{p}$), where C is a constant factor and estimated the best-fit parameter $p$ using non-linear least squares fitting with `scipy`’s `curve_fit`." (Core Growth and CMF)
   - validation: Compared best-fit power-law infall model against BHL accretion, clump-fed model (Tan et al. 2014), and tidal-lobe accretion predictions  
  > "We compare the estimated value with theoretical predictions. One is the clump-fed model derived by (cite: Tan14) as their Equation (16)" (Core Growth and CMF)

## Software

- **Astropy** : General astronomical data analysis  
  > "Astropy (cite: Astropy_13; Astropy18; Astropy22), astrodendro (cite: Rosolowsky08), CASA (cite: CASA22), getsf (cite: Menshchikov13; Menshchikov21), Matplotlib (cite: Hunter_matplotlib), Numpy (cite: Harris20_numpy), powerlaw (cite: Alstott14), Scipy (cite: Virtanen_scipy), seaborn (cite: Waskom2021_seaborn)." (Software)
- **astrodendro** : Dendrogram core identification on 1.3 mm continuum images and completeness/flux recovery simulations  
  > "By applying the dendrogram technique, implemented in `astrodendro` (cite: Rosolowsky08), to the 1.3 mm continuum images of 39 regions, we have identified 839 cores (cite: Morii23)." (Observations and Data); "We also measured how much flux was recovered by the dendrogram algorithm by comparing the flux of leaves identified by `astrodendro` and the inserted flux." (Completeness)
- **CASA** : Listed in Software section  
  > "Astropy (cite: Astropy_13; Astropy18; Astropy22), astrodendro (cite: Rosolowsky08), CASA (cite: CASA22), getsf (cite: Menshchikov13; Menshchikov21), Matplotlib (cite: Hunter_matplotlib), Numpy (cite: Harris20_numpy), powerlaw (cite: Alstott14), Scipy (cite: Virtanen_scipy), seaborn (cite: Waskom2021_seaborn)." (Software)
- **getsf** : Alternative core identification on 39 continuum images to test robustness of astrodendro results  
  > "To confirm our results are independent of the core identification method adopted (astrodendro), we ran `getsf` (cite: Menshchikov13; Menshchikov21), as described in Appendix [7](#sec:Appendix_coremethod), and obtain a consistent result." (Completeness)
- **Matplotlib** : Plotting  
  > "Astropy (cite: Astropy_13; Astropy18; Astropy22), astrodendro (cite: Rosolowsky08), CASA (cite: CASA22), getsf (cite: Menshchikov13; Menshchikov21), Matplotlib (cite: Hunter_matplotlib), Numpy (cite: Harris20_numpy), powerlaw (cite: Alstott14), Scipy (cite: Virtanen_scipy), seaborn (cite: Waskom2021_seaborn)." (Software)
- **Numpy** : Determining histogram bin edges using Freedman Diaconis Estimator (fd)  
  > "The bin size was determined with a task in `numpy` of *histogram bin edges* as Freedman Diaconis Estimator (fd), which takes into account data size." (Core Mass)
- **powerlaw** : Maximum likelihood estimation (MLE) fitting of CMF power-law slopes  
  > "Also, we performed the fitting using maximum likelihood estimates (MLE; Figures [3](#fig:cmf_prebound) (c) and (f)) as developed by (cite: Clauset09), following one of the ALMA-IMF studies by (cite: Louvet24) and implemented in the Python package, `powerlaw` (cite: Alstott14)." (Prestellar CMF)
- **Scipy** : Non-linear least squares fitting (curve_fit) of core mass infall power-law parameters  
  > "Then, to investigate which power-law index of mass can reproduce the observed CMFs, we assumed that the external mass infall rate follows a power-law dependence on mass ($\dot{M} = C M^{p}$), where C is a constant factor and estimated the best-fit parameter $p$ using non-linear least squares fitting with `scipy`’s `curve_fit`." (Core Growth and CMF)
- **seaborn** : Statistical data visualization  
  > "Astropy (cite: Astropy_13; Astropy18; Astropy22), astrodendro (cite: Rosolowsky08), CASA (cite: CASA22), getsf (cite: Menshchikov13; Menshchikov21), Matplotlib (cite: Hunter_matplotlib), Numpy (cite: Harris20_numpy), powerlaw (cite: Alstott14), Scipy (cite: Virtanen_scipy), seaborn (cite: Waskom2021_seaborn)." (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total cores identified in 39 clumps | 839 | not stated | cores | 1 | By applying the dendrogram technique, implemented in `astrodendro` (cite: Rosolowsky08), to the 1.3 mm continuum images of 39 regions, we have identified 839 cores (cite: Morii23). |
| Final selected core sample size (34 clumps) | 715 | not stated | cores | 3 | After this selection, our sample ensures a 90% completeness level above 1.2 $M_\odot$, resulting in a final sample of 715 cores for the CMF analysis. |
| Prestellar core candidates in selected sample | 461 | not stated | cores | 3 | Among the 715 cores in the middle panel, the numbers of prestellar core candidates, warm cores, and outflow cores are 461, 178, and 76, respectively. |
| Protostellar cores in selected sample | 254 | not stated | cores | 3 | We study the CMF in the earliest stage of high-mass star formation using 461 prestellar core candidates and 254 protostellar cores as a part of the ALMA Survey of 70 μm Dark High-mass Clumps in Early Stages (ASHES). |
| Gravitationally bound prestellar cores in selected sample | 130 | not stated | cores | 3 | Our prestellar core sample consists of 461 cores without any signs of protostars detected by ALMA such as molecular outflows and warm gas tracers. It includes 130 gravitationally bound cores based on virial analysis. |
| Derived core mass range | 0.06 to 81 | ~50% | M_sun | 2 | The derived core mass ranges from 0.06 to 81 $M_\odot$. The uncertainties of mass is $\sim$50%, largely contributed from the gas-to-dust mass ratio and the dust opacity (cite: Morii23). |
| 90% mass completeness level across all 39 clumps | 0.3-4.5 (median ~0.6) | not stated | M_sun | 3 | The completeness level ranges from 0.3–4.5 $M_\odot$ with a median of $\sim$0.6 $M_\odot$. |
| 90% mass completeness threshold for selected 34 clumps | 1.2 | not stated | M_sun | 3 | After this selection, our sample ensures a 90% completeness level above 1.2 $M_\odot$, resulting in a final sample of 715 cores for the CMF analysis. |
| CMF power-law slope (all selected cores, differential histogram before flux correction) | -1.92 | 0.12 | dimensionless | 4 | As expected from the recovered flux plot, the flux correction mostly affects low-mass cores near 1 $M_\odot$, and it makes a slightly steeper slope from -1.92$\pm$0.12 to -2.02$\pm$0.11. |
| CMF power-law slope (all selected cores, differential histogram after flux correction) | -2.02 | 0.11 | dimensionless | 4 | As expected from the recovered flux plot, the flux correction mostly affects low-mass cores near 1 $M_\odot$, and it makes a slightly steeper slope from -1.92$\pm$0.12 to -2.02$\pm$0.11. |
| CMF power-law slope (all selected cores, MLE) | -2.05 | 0.04 | dimensionless | 4 | The CMF, including both protostellar and prestellar cores, has a power-law slope of -2.05$\pm$0.04, shallower than Salpeter’s IMF slope of -2.35.; Since they used the MLE method, to directly compare with our sample, we also plot the best-fit index derived in the same way as a gray line ($\alpha=$-2.05$\pm$0.04). |
| CMF power-law slope (gravitationally bound prestellar cores, MLE) | -2.32 | 0.30 | dimensionless | 4 | Conversely, the CMF of gravitationally bound, prestellar cores has a steeper slope (-2.32$\pm$0.30), indistinguishable from Salpeter’s slope. |
| CMF power-law slope range (prestellar core candidates across methods) | -2.65 to -2.38 | not stated | dimensionless | 4 | The best fit $\alpha$ was -2.65 to -2.38 for prestellar core candidates (including bound and unbound cores) and -2.53 to -1.83 for bound prestellar cores. |
| CMF power-law slope range (gravitationally bound prestellar cores across methods) | -2.53 to -1.83 | not stated | dimensionless | 4 | The best fit $\alpha$ was -2.65 to -2.38 for prestellar core candidates (including bound and unbound cores) and -2.53 to -1.83 for bound prestellar cores. |
| Statistical lifetime of bound prestellar cores | 0.18 | not stated | Myr | 5 | By inserting the total number of bound, prestellar cores and the number of bound, protostellar cores (including both warm cores and outflow cores) into Equation [\[equ:lifetime\]](#equ:lifetime), we estimate the lifetime of prestellar cores to be 0.18 Myr. |
| External mass infall rate power-law exponent (p) | 1.16 | 0.02 | dimensionless | 6 | The derived best-fit parameter is $p=1.16\pm0.02$ with $C=1.60\pm$0.01. |
| External mass infall rate normalization factor (C) | 1.60 | 0.01 | dimensionless | 6 | The derived best-fit parameter is $p=1.16\pm0.02$ with $C=1.60\pm$0.01. |
| External mass infall rate at 1 M_sun (assuming 30 kyr infall duration) | 5.33e-5 | not stated | M_sun yr^-1 | 6 | Assuming a duration of external infall of 30 kyr, approximately free-fall time of ASHES cores, the mass infalll rate is described as $$egin{equation} \dot{M}= 5.33	imes 10^{-5} \left( rac{M_{m core}}{1\,M_\odot} ight)^{1.16} \,M_\odot\,{m yr^{-1}}. \label{equ:bestfit-mdot} \end{equation}$$ |
| Cores identified by getsf in 39 clumps | 331 | not stated | cores | 1 | As a result, 331 cores were identified from 39 clumps. Of those, 305 overlap with the cores identified by `astrodendro` according to their positions. |
| CMF power-law slope using getsf cores | -1.78 | 0.12 | dimensionless | 4 | The power-law fit was applied to the CMFs with $M > 1.2 M_\odot$, and the best-fit parameters are $\alpha = -1.92\pm0.12$ and $-1.78\pm0.12$ for `astrodendro` and `getsf`, respectively. |

## Qualitative findings

- Prestellar core candidates generally have lower masses than protostellar cores, and the fraction of protostellar cores increases with core mass.  
  > "We find that prestellar core candidates tend to have lower masses than protostellar cores." (Abstract); "This plot clearly shows the increase of the percentage of protostellar cores as core mass increases." (Core Mass)
- The prestellar CMF has a Salpeter-like slope consistent across low-mass star-forming regions and massive protoclusters, implying a universal core formation mechanism.  
  > "The power-law index of the prestellar CMFs is similar to those derived in low-mass star-forming regions and also in more evolved, massive protoclusters. This implies a universal core formation mechanism to produce the mass distribution between low- and high-mass star-forming regions." (Conclusion)
- The lifetime of prestellar cores decreases with increasing core mass, approaching the freefall time at ~10 M_sun unless significant core growth occurs.  
  > "This lifetime decreases as the core mass increases and approaches the freefall time at $M_{m core} \sim$10 $M_\odot$." (Conclusion)

## Claim tuples

- H: The mass distribution of prestellar cores in early-stage high-mass star-forming clumps follows a universal Salpeter-like power-law slope, whereas including protostellar cores produces a shallower top-heavy slope. | E: Constructed CMFs for 715 cores (461 prestellar candidates, 130 gravitationally bound prestellar cores, and 254 protostellar cores) above the 90% completeness limit of 1.2 M_sun using differential histograms, variable-bin cumulative distributions, and unbinned MLE fitting. | R: The combined CMF has an MLE slope of -2.05+-0.04 (shallower than -2.35), while the gravitationally bound prestellar CMF has an MLE slope of -2.32+-0.30 (spanning -2.65 to -2.38 for all prestellar candidates and -2.53 to -1.83 for bound prestellar cores across methods). | F: The prestellar CMF is indistinguishable from Salpeter's IMF slope (-2.35), supporting a universal core formation mechanism, while the shallower full CMF reflects star formation activity and core growth. | **supported**
- H: Prestellar core lifetimes in IRDCs are longer than the freefall time and depend on core mass. | E: Calculated the statistical lifetime of gravitationally bound prestellar cores relative to bound protostellar cores assuming a protostellar lifetime of 0.2 Myr, both for the whole sample and in logarithmic mass bins. | R: The overall bound prestellar lifetime is 0.18 Myr (~6 times the freefall time of ~3x10^4 yr), decreasing from ~1 Myr at low masses to <=0.1 Myr (approaching the freefall time) as core mass increases toward 10 M_sun. | F: Prestellar cores generally live a few times longer than their freefall time in the 1-5 M_sun range, while more massive cores collapse on near-freefall timescales unless substantial core mass growth occurs. | **supported**
- H: The shallower protostellar CMF and higher maximum core mass arise from external gas infall (core growth) onto prestellar cores. | E: Modeled the evolution from the bound prestellar CMF to the bound protostellar CMF using Bondi-Hoyle-Lyttleton (BHL) accretion and a fitted power-law mass infall rate (M_dot = C * M^p). | R: BHL accretion requires ~1.5 Myr and yields an overly shallow CMF, whereas a power-law infall model with p = 1.16+-0.02 and M_dot = 5.33x10^-5 (M_core / 1 M_sun)^1.16 M_sun yr^-1 over 30 kyr reproduces the observed protostellar CMF. | F: Core growth driven by external gas infall at rates higher and with a shallower mass dependence than BHL accretion (more consistent with clump-fed or tidal-lobe accretion) can transform the Salpeter-like prestellar CMF into the shallower protostellar CMF. | **supported**

## Reasoning

- Why this data: 70 μm-dark IRDC clumps trace the earliest stages of high-mass star and cluster formation before feedback disrupts the environment, and the ASHES survey provides a large, well-characterized sample of 839 cores.  
  > "The CMF within IRDCs likely reflects the mass distribution of cores during the early stages of cluster evolution." (Introduction); "In the ALMA Survey of 70 μm Dark High-Mass Clumps in Early Stages (ASHES), we obtained the large, extremely well-characterized population of cores embedded in the IRDCs (cite: Sanhueza19; Li20; Tafoya21; Morii21; Li22; Sabatini22; Sakai22; Li23; Morii23; Izumi24; Morii24; Lin25)." (Introduction)
- Why this method: Used astrodendro because prior work demonstrated higher detection completeness and better parameter extraction; used variable-bin cumulative distributions and unbinned MLE fitting to avoid histogram binning biases and allow direct comparison with ALMA-IMF studies.  
  > "(cite: LiChong20_identification) demonstrated that the `astrodendro` has higher detection completeness and better performance in extracting parameters (e.g., size, mass, and flux) than other algorithms such as `ClumpFind` and `GaussClumps`." (Core Identification: astrodendro VS getsf); "MLE determines the best-fit power-law slope directly from the unbinned data by maximizing the likelihood of the observed distribution, avoiding biases from histogram binning." (Prestellar CMF)
- Alternative: Core identification with getsf instead of astrodendro (tested in Appendix and shown to yield consistent shallow CMF slope)  
  > "To confirm our results are independent of the core identification method adopted (astrodendro), we ran `getsf` (cite: Menshchikov13; Menshchikov21), as described in Appendix [7](#sec:Appendix_coremethod), and obtain a consistent result." (Completeness)
- Alternative: Bondi-Hoyle-Lyttleton (BHL) accretion to explain CMF evolution (rejected as sole mechanism because required timescale is ~1.5 Myr and resulting CMF is too shallow)  
  > "The timescale needed for this model is comparable to the inertial inflow model proposed by (cite: Padoan20), although it is much longer than the prestellar lifetime estimated in Section [4.2](#subsec:lifetime). The CMF became shallower as the accretion rate is proportional to mass squared, and it is much shallower than the observed protostellar CMF (red line)." (Core Growth and CMF)
- Alternative: Decreasing core mass over time due to protostellar accretion (M_proto = 2 * M_obs) vs. increasing core mass due to clump infall (M_proto = 0.5 * M_obs) in lifetime estimates  
  > "First, let us consider a scenario where the core mass decreases over time due to accretion onto the forming protostar." (Lifetime of Prestellar Cores); "Alternatively, the core mass may increase during its evolution as discussed in Section [4.3](#sec:core-growth)." (Lifetime of Prestellar Cores)
- How they decided it was enough: _not stated_
- Limitation (authors): Core mass uncertainties are ~50%, largely from gas-to-dust mass ratio and dust opacity.  
  > "The uncertainties of mass is $\sim$50%, largely contributed from the gas-to-dust mass ratio and the dust opacity (cite: Morii23)." (Core Mass)
- Limitation (authors): Reference protostellar lifetime (0.2 Myr) has an uncertainty of about a factor of two, and the statistical lifetime analysis assumes a constant star formation rate within each clump.  
  > "As discussed in (cite: Valeille-Manet25), this has an uncertainty of about a factor of two." (Lifetime of Prestellar Cores); "One caveat of this analysis is that we assumed that the star formation rate (SFR) remains constant within each clump. If the SFR at the current stage is low, the derived lifetime may be overestimated." (Lifetime of Prestellar Cores)
- Limitation (authors): Limited sample size at the high-mass end causes the best-fit power-law index to depend slightly on the CMF representation and restricts discussion of later evolution from top-heavy CMF back to Salpeter IMF.  
  > "This figure shows that the power-law index $\alpha$ slightly depends on the representations of the mass distribution in such a limited sample size at the high-mass end." (Prestellar CMF); "The evolution from a top-heavy CMF to Salpeter’s IMF has not been discussed in this paper, primarily because our targets are in the similar evolutionary stages and the sample of protostellar cores is small." (Core Growth and CMF)
- Limitation (authors): Virial analysis ignores external pressure and magnetic fields.  
  > "Among 839 cores, either of the lines is detected from 492 cores (58.6%), and 340 cores (69.1%) have virial parameter smaller than 2, classified as gravitationally bound cores ignoring external pressure and the magnetic field (cite: Morii24)." (Observations and Data)
- Caveat (inferred, ours): Exclusion of 5 clumps with poorer completeness removes 5 out of the 7 most massive cores (>25 M_sun, mostly in G028.564-00.236), which could affect the high-mass tail of the full CMF.
- Caveat (inferred, ours): Dust temperatures for 28 of the 39 clumps are assumed to be constant clump-averaged values rather than core-resolved temperatures; local heating in protostellar cores (warm/outflow cores) could lead to overestimated protostellar core masses and artificially flatten the protostellar CMF.

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: FITS continuum images of the 39 ASHES clumps to run astrodendro, getsf, and the artificial Gaussian core completeness simulations
- Missing: Exact astrodendro parameters (min_value, min_delta, min_npix) used during the 5000-trial completeness and flux recovery tests
- Missing: Region-by-region flux recovery curves used to correct individual core masses
- Data volume (inferred): A few GB for the 39 continuum maps and catalog tables (or ~100-500 GB if re-imaging raw ALMA visibilities across 3 cycles).
- Score (inferred): 75/5, The statistical, CMF fitting, completeness, lifetime, and infall modeling steps are clearly described with standard Python packages (astrodendro, powerlaw, scipy, numpy), and the core catalogs/temperatures are published in companion papers (Morii et al. 2023, 2024), though exact astrodendro thresholds and the FITS continuum maps are needed to exactly replicate the injection-recovery flux corrections.
- Rediscovery candidate: yes, The ALMA datasets (Cycles 3, 5, 6) and companion catalogs (Morii et al. 2023, 2024) are public, the core extraction and power-law fitting recipes are well-specified, and the main results are concrete numerical slopes, lifetimes, and infall parameters.

## Links

- Method: (cite: Rosolowsky08) (Dendrogram algorithm (astrodendro) used for core identification and completeness simulations)
- Method: (cite: Menshchikov13; Menshchikov21) (getsf source extraction algorithm used to validate core identification and CMF slope)
- Method: (cite: MaizApellaniz05) (Variable-size binning method for cumulative mass distributions)
- Method: (cite: Reid06) (Complementary cumulative distribution methodology for CMF fitting)
- Method: (cite: Clauset09) (Maximum likelihood estimation (MLE) method for unbinned power-law fitting)
- Method: (cite: Alstott14) (Python powerlaw package implementing MLE fitting)
- Method: (cite: Pouteau22) (First-order optical depth check at 1.3 mm)
- Companion: (cite: Sanhueza19) (ASHES pilot survey paper describing observation setup and initial CMF analysis)
- Companion: (cite: Morii21) (Earlier ASHES paper on core classification and dense/warm gas tracers)
- Companion: (cite: Morii23) (ASHES paper providing the 839 continuum core catalog, clump properties, and dust temperatures)
- Companion: (cite: Morii24) (ASHES paper providing the molecular line classifications (outflow/warm/prestellar) and virial parameters for the 839 cores)
- Companion: (cite: Li20) (ASHES series paper on molecular outflows)
- Companion: (cite: Li23) (ASHES series paper on NH3 temperatures and virial analysis)
- Companion: (cite: Izumi24) (ASHES series paper on warm gas tracers and outflows)
- Companion: (cite: Morii25) (GLASHES survey paper on core-scale mass infall rates in the ASHES sample)
- Related: ASHES (ALMA Survey of 70 μm Dark High-mass Clumps in Early Stages)
- Related: GLASHES (Global and Local Infall in the ASHES Sample)
- Related: ALMA-IMF
- Related: ALMAGAL
- Related: QUARKS
- Related: SQUALO

## Checks

```json
{
 "quotes": 143,
 "quotes_ok": 143,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 16,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 20,
 "numeric_problems": 0,
 "fill": {
  "facts": 118,
  "stated": 70,
  "rate": 0.593
 },
 "evidence_ok": true
}
```
